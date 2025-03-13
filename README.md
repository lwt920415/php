        person: function(_id, _path) {
                this.load = layer.load(1);
                $.post(_path + "index.php/index/person", {
                        id: _id
                },
                function(data) {
                        layer.close(min.load);
                        var obj = JSON.parse(data);
                        if (obj.state == 1) {
                                var _html = '<p style="text-align:center;padding-top:20px"><img src="http://127.0.0.1/client/view/index/css/avatar.png" height="80" width="80" style="border-radius:50%"></p>';
                                _html += '<p style="word-wrap:break-word;max-width:300px;padding:5px 30px 0 30px"><b>邮箱帐号：</b>6@qq.com</p>';
                                _html += '<p style="max-width:300px;padding:5px 30px 0 30px"><b>积分余额：</b>99</p>';
                                _html += '<p style="max-width:300px;padding:5px 30px 0 30px"><b>认证状态：</b>待审核</p>';
                                _html += '<p style="word-wrap:break-word;max-width:300px;padding:5px 30px 0 30px"><b>个人昵称：</b>136245992</p>';
                                _html += '<p style="max-width:300px;padding:5px 30px 0 30px"><b>个人手机：</b>15257534992</p>';
                                _html += '<p style="word-wrap:break-word;max-width:300px;padding:5px 30px 0 30px"><b>个人链接：</b>https://</p>';
                                _html += '<p style="word-wrap:break-word;max-width:300px;padding:5px 30px 20px 30px"><b>个人简介：</b></p>';
                                layer.open({
                                        type: 1,
                                        area: ["auto", "auto"],
                                        title: "个人名片",
                                        content: _html
                                })
                        } else if (obj.state == -1) {
                                layer.msg("用户不存在！", {
                                        icon: 5
                                })
                        } else {
                                layer.msg(obj.state, {
                                        time: 0,
                                        btn: ["确定"]
                                })
                        }
                })
        }
