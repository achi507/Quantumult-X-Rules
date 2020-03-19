# Quantumult-X-Rules
QX规则自用
规则整合神机规则和lhie1规则，感谢以上规则作者分享！

Remove weibo ads

[rewrite_local]
^https?://(sdk|wb)app\.uve\.weibo\.com(/interface/sdk/sdkad.php|/wbapplua/wbpullad.lua) url script-response-body wb_launch.js
^https?://m?api\.weibo\.c(n|om)/2/(statuses/(unread|extend|positives/get|(friends|video)(/|_)(mix)?timeline)|stories/(video_stream|home_list)|(groups|fangle)/timeline|profile/statuses|comments/build_comments|photo/recommend_list|service/picfeed|searchall|cardlist|page|!/photos/pic_recommend_status) url script-response-body wb_ad.js
[mitm]
hostname = api.weibo.cn, mapi.weibo.com, *.uve.weibo.com


Display jd historical price

[rewrite_local]
^https?://api\.m\.jd\.com/client\.action\?functionId=(wareBusiness|serverConfig) url script-response-body jd_price.js
[mitm]
hostname = api.m.jd.com
Display taobao historical price

# 不生效或失效的需要卸载 tb 重装，注意不开脚本进 tb 会失效
[rewrite_local]
^http://amdc\.m\.taobao\.com/amdc/mobileDispatch url script-response-body tb_price.js
^https?://trade-acs\.m\.taobao\.com/gw/mtop\.taobao\.detail\.getdetail url script-response-body tb_price.js
[mitm]
hostname = trade-acs.m.taobao.com

# 以上还不生效或者频繁失效的可以添加以下规则，使用规则有可能误伤其他功能或者应用（一般不需要添加规则就能正常使用）
# [filter_local]
# ip-cidr, 203.119.144.0/23, reject
# ip-cidr, 203.119.175.0/24, reject
# ip-cidr, 106.11.162.0/24, reject
# ip-cidr, 47.102.83.0/24, reject

