<?php 
ob_start();

$token = "5811267819:AAFaM5_eko3I99iwvICwlwRyZFBGd_JMFVM"; # Token
define("API_KEY", $token);
echo "setWebhook ~> <a href=\"https://api.telegram.org/bot".API_KEY."/setwebhook?url=".$_SERVER['SERVER_NAME']."".$_SERVER['SCRIPT_NAME']."\">https://api.telegram.org/bot".API_KEY."/setwebhook?url=".$_SERVER['SERVER_NAME']."".$_SERVER['SCRIPT_NAME']."</a>";
function bot($method,$datas=[]){
$url = "https://api.telegram.org/bot".API_KEY."/".$method;
$ch = curl_init();
curl_setopt($ch,CURLOPT_URL,$url);
curl_setopt($ch,CURLOPT_RETURNTRANSFER,true);
curl_setopt($ch,CURLOPT_POSTFIELDS,$datas);
$res = curl_exec($ch);
if(curl_error($ch)){
var_dump(curl_error($ch));
}else{
return json_decode($res);
}}




# Short
$update = json_decode(file_get_contents("php://input"));
$message = $update->message;
$txt = $message->caption;
$text = $message->text;
$chat_id = $message->chat->id;
$from_id = $message->from->id;
$new = $message->new_chat_members;
$message_id = $message->message_id;
$type = $message->chat->type;
$name = $message->from->first_name;
if(isset($update->callback_query)){
$callbackMessage = '';
var_dump(bot('answerCallbackQuery',[
'callback_query_id'=>$update->callback_query->id,
'text'=>$callbackMessage]));
$up = $update->callback_query;
$chat_id = $up->message->chat->id;
$from_id = $up->from->id;
$user = $up->from->username;
$name = $up->from->first_name;
$message_id = $up->message->message_id;
$data = $up->data;
}
$id = $update->inline_query->from->id; 
$sud = file_get_contents("admin.txt");

$sudo = array("00000","00000","00000","$sudo","220218136");
//$wathq1 = $sud; 
$wathq1 = 220218136; #ايدي حسابك
mkdir("sudo");
mkdir("message");
mkdir("data");
mkdir("ms");
mkdir("count");
mkdir("count/user");
mkdir("count/admin");
$START= file_get_contents("data/start.txt");
$getmes_id = explode("\n", file_get_contents("ms/$message_id.txt"));
$get_ban=file_get_contents('data/ban.txt');
$ban =explode("\n",$get_ban);
/////////////////////

$member = explode("\n",file_get_contents("sudo/member.txt"));
$cunte = count($member)-1;
//////////

$amr = file_get_contents("sudo/amr.txt");
$ch1 = file_get_contents("sudo/ch1.txt");
$ch2= file_get_contents("sudo/ch2.txt");
$taf3il = file_get_contents("sudo/tanbih.txt");
$estgbal = file_get_contents("sudo/estgbal.txt");

 //ايديك
$reply = $message->reply_to_message->message_id;
$rep = $message->reply_to_message->forward_from; 

////======================\\\\

if($message){
$join = file_get_contents("https://api.telegram.org/bot$token/getChatMember?chat_id=$ch1&user_id=$from_id");
$join2 = file_get_contents("https://api.telegram.org/bot$token/getChatMember?chat_id=$ch2&user_id=$from_id");

if($message && (
strpos($join,'"status":"left"') 
or
strpos($join,'"Bad Request: USER_ID_INVALID"')
or
strpos($join,'"Bad Request: user not found"')
or
strpos($join,'"ok": false')
or strpos($join,'"status":"kicked"') or 
strpos($join2,'"status":"left"') 
or 
strpos($join2,'"Bad Request: USER_ID_INVALID"') 
or 
strpos($join2,'"Bad Request: user not found"') 
or
strpos($join2,'"ok": false') 
or strpos($join2,'"status":"kicked"'))!== false){
$ch1=str_replace("@","",$ch1);
$ch2=str_replace("@","",$ch2);
bot('sendMessage',[
'chat_id'=>$chat_id,
'reply_to_message_id'=>$message_id,
'text'=>"
⛔️| عذرا عزيزي
◾| البوت لا يعمل الا اذا قمت بالاشتراك بالقناه
◾| وعند الغاء الاشتراك فان البوت سوف يتوقف


[📨|اضعط للاشتراك في القناة الاولى 💘💌'](https://t.me/$ch1)

[📨|اضعط للاشتراك في القناة الثانية 💘💌'](https://t.me/$ch2)
",
'disable_web_page_preview'=>true,
'parse_mode'=>"markdown",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"• اضغط للاشتراك في القناة الاولى", 'url'=>"https://t.me/$ch1"]],
[['text'=>"• اضغط للاشتراك في القناة الثانية", 'url'=>"https://t.me/$ch2"]]
]
])
]);
return false;}}





if($update and !in_array($from_id, $member)){
file_put_contents("sudo/member.txt","$from_id\n",FILE_APPEND);

if($taf3il == "yas" ){
bot("sendmessage",[
"chat_id"=>$wathq1,
"text"=>"- دخل شخص إلى البوت 🚶‍♂

[$name](tg://user?id=$from_id) 

- ايديه $from_id 🆔

---------
عدد اعضاء بوتك هو : $cunte
",
'disable_web_page_preview'=>'true',
'parse_mode'=>"markdown",
]);
}else{
bot("sendmessage",[
"chat_id"=>$wathq1,
"text"=>"",
]);
}}
if($data=="admin"and in_array($from_id, $sudo)){
bot('EditMessageText',[
'chat_id'=>$chat_id,
'message_id'=>$message_id,
"text"=>"👮|  اهلا بك عزيزي المطور اليك قائمة الاوامر الشفافة قم باختيار ",
'reply_markup'=>json_encode([ 
'inline_keyboard'=>[
[['text'=>'- أوامر قناة الإشتراك الإجباري الأولى 📡1⃣".' ,'callback_data'=>"ula"]],

[['text'=>'- أوامر قناة الإشتراك الإجباري الثانية 📢2⃣".' ,'callback_data'=>"thany"]],

[['text'=>'- عرض قنوات الإشتراك الإجباري 📜".' ,'callback_data'=>"gnoaty"]],
[['text'=>'- أوامر البيانات الخاصة بالمالك 🗣".' ,'callback_data'=>"atther"]],

[['text'=>'- أوامر الإذاعة 🗣".' ,'callback_data'=>"ethaa"]],

[['text'=>'- عدد المشتركين 👥".' ,'callback_data'=>"memb"]],

[['text'=>'- التنبيه عند دخول أحد للبوت 🚸".' ,'callback_data'=>"tnbeh"]],

[['text'=>'-عدد المحضورين 👥".' ,'callback_data'=>"ban"]],


[['text'=>'- استقبال الرسائل من الأعضاء 🔃".' ,'callback_data'=>"estgbal"]],
[['text'=>'الحمايــــــــــــه 🔒' ,'callback_data'=>"hmaih"]],
   ] 
   ])
]);
unlink("sudo/amr.txt");

}
if($text=="م"and in_array($from_id, $sudo)){
bot('sendmessage',[
'chat_id'=>$chat_id,
'message_id'=>$message_id,
"text"=>"👮|  اهلا بك عزيزي المطور اليك قائمة الاوامر الشفافة قم باختيار ",
'reply_markup'=>json_encode([ 
'inline_keyboard'=>[
[['text'=>'- أوامر قناة الإشتراك الإجباري الأولى 📡1⃣".' ,'callback_data'=>"ula"]],

[['text'=>'- أوامر قناة الإشتراك الإجباري الثانية 📢2⃣".' ,'callback_data'=>"thany"]],

[['text'=>'- عرض قنوات الإشتراك الإجباري 📜".' ,'callback_data'=>"gnoaty"]],
[['text'=>'- أوامر البيانات الخاصة بالمالك 🗣".' ,'callback_data'=>"atther"]],

[['text'=>'- أوامر الإذاعة 🗣".' ,'callback_data'=>"ethaa"]],

[['text'=>'- عدد المشتركين 👥".' ,'callback_data'=>"memb"]],

[['text'=>'- التنبيه عند دخول أحد للبوت 🚸".' ,'callback_data'=>"tnbeh"]],

[['text'=>'-عدد المحضورين 👥".' ,'callback_data'=>"ban"]],


[['text'=>'- استقبال الرسائل من الأعضاء 🔃".' ,'callback_data'=>"estgbal"]],
[['text'=>'الحمايــــــــــــه 🔒' ,'callback_data'=>"hmaih"]],
   ] 
   ])
]);
unlink("sudo/amr.txt");

}
///====قنوات الاشتراك الاجباري ====\\\\


if($data == "ula"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- أوامر قناة الإشتراك الإجباري الأولى 📡1⃣".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- وضع قناة 📡✅".' ,'callback_data'=>"ch1"]],
[['text'=>'- حذف القناة 📡❎".' ,'callback_data'=>"dch1"]],[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]
])
]);
}

if($data == "ch1"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- أرسل معرف القناة الآن Ⓜ️".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- إلغاء ❌".' ,'callback_data'=>"ula"]],
]])
]);
file_put_contents("sudo/amr.txt","ch1");
}
if($text and $amr == "ch1" and $from_id == $wathq1){
bot("sendmessage",[
"chat_id"=>$chat_id,
"text"=>'- تم حفظ معرف القناة الاولى بنجاح ✅".

- تأكد من أن البوت أدمن في القناة ليتم تفعيل الإشتراك الإجباري 👨🏻‍✈️".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
file_put_contents("sudo/ch1.txt","$text");
unlink("sudo/amr.txt");
}
if($data == "dch1"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم حذف القناة بنجاح ✅".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
unlink("sudo/amr.txt");
unlink("sudo/ch1.txt");
}
/////////////////2/////////////////
if($data == "thany"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- أوامر قناة الإشتراك الإجباري الثانية 📢2⃣".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- وضع قناة 📡✅".' ,'callback_data'=>"ch2"]],
[['text'=>'- حذف القناة 📡❎".' ,'callback_data'=>"dch2"]],[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]
])
]);
}
if($data == "ch2"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- أرسل معرف القناة الآن Ⓜ️".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- إلغاء ❌".' ,'callback_data'=>"thany"]],
]])
]);
file_put_contents("sudo/amr.txt","ch2");
}
if($text and $amr == "ch2" and $from_id == $wathq1){
bot("sendmessage",[
"chat_id"=>$chat_id,
"text"=>'- تم حفظ معرف القناة الثانية بنجاح ✅".

- تأكد من أن البوت أدمن في القناة ليتم تفعيل الإشتراك الإجباري 👨🏻‍✈️".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
file_put_contents("sudo/ch2.txt","$text");
unlink("sudo/amr.txt");
}
if($data == "dch2"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم حذف القناة بنجاح ✅".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
unlink("sudo/amr.txt");
unlink("sudo/ch2.txt");
}


///////////////3/////////////////
if($data == "gnoaty"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- هذه هي قائمة قنوات الإشتراك الإجباري 📜".

- القناة الأولى '.$ch1.' 📡".

- القناة الثانية '.$ch2.' 📢".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
unlink("sudo/amr.txt");
}

///==== الاذاعة  ====\\\\

///==== الاذاعة  ====\\\\
$memberi = explode("\n",file_get_contents("sudo/member.txt"));
$cuntei = count($memberi)-1;

if($data == "ethaa"){
$mim= file_get_contents("sudo/member.txt");
file_put_contents("sudo/mim.txt","$mim");
mkdir("ms");
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- أوامــــــــر الإذاعــــــــــــــــة 🗣".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- نشر توجيه ↪️".' ,'callback_data'=>"tawgih"]],
[['text'=>'-MARKDOWN نشر رسالة 📝".' ,'callback_data'=>"messagem"]],
[['text'=>'-HTML نشر رسالة 📝".' ,'callback_data'=>"messageh"]],
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]
])
]);
}


$miim = explode("\n",file_get_contents("sudo/mim.txt"));
$cmiim = count($miim)-1;
/////////////////markdown
if($data == "messagem"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>"- أرسل رسالتك ليتم نشرها بصيغة markdown رسالة لجميع الأعضاء 📝 
عدد الاعضاء : $cmiim
",
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- إلغاء ❌".' ,'callback_data'=>"ethaa"]],
]])
]);
file_put_contents("sudo/amr.txt","messagemark");
}

if($text and $amr == "messagemark" and in_array($from_id, $sudo)){
unlink("sudo/amr.txt");
bot("sendMessage",[
"chat_id"=>$chat_id,
"text"=>"$text",
"message_id"=>$message_id+1,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true
]);
$msg = $message_id+1;
for($i=0;$i<count($miim);$i++){
$get =bot('SendMessage', [
'chat_id' => $miim[$i],
'text'=>$text,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true
]);
$msg_id = $get->result->message_id;
file_put_contents("ms/$msg.txt",$miim[$i]."==". $msg_id."\n", FILE_APPEND);
$str= file_get_contents("sudo/mim.txt");
$str= str_replace($miim[$i]."\n","",$str);
file_put_contents("sudo/mim.txt",$str);
}
$ms=explode("\n",file_get_contents("ms/$msg.txt"));
$count= count($ms);

bot("sendMessage",[
"chat_id"=>$chat_id,
"text"=>"- تم نشر هذه الرساله 👇
-----------------------------------
$text
-----------------------------------
لعدد ($count) عضو. * 
",

"message_id"=>$message_id+1,
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"حذف الرسالة",'callback_data'=>"delelink ".$msg]],
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"ethaa"]],
]])
]);
}

//////////////html
if($data == "messageh"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- أرسل رسالتك ليتم نشرها بصيغة HTML رسالة لجميع الأعضاء 📝".
عدد الاعضاء:'.$cmiim,
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- إلغاء ❌".' ,'callback_data'=>"ethaa"]],
]])
]);
file_put_contents("sudo/amr.txt","messagehtml");
}
if($text and $amr == "messagehtml" and in_array($from_id, $sudo)){
unlink("sudo/amr.txt");
bot("sendMessage",[
"chat_id"=>$chat_id,
"text"=>"$text",
"message_id"=>$message_id+1,
]);
$msg = $message_id+1;
for($i=0;$i<count($miim);$i++){
$get =bot('SendMessage', [
'chat_id' => $miim[$i],
'text'=>$text,
'parse_mode'=>"html",
'disable_web_page_preview'=>true
]);
$msg_id = $get->result->message_id;
file_put_contents("ms/$msg.txt",$miim[$i]."==". $msg_id."\n", FILE_APPEND);
$str= file_get_contents("sudo/mim.txt");
$str= str_replace($miim[$i]."\n","",$str);
file_put_contents("sudo/mim.txt",$str);
}
$ms=explode("\n",file_get_contents("ms/$msg.txt"));
$count= count($ms);

bot("sendMessage",[
"chat_id"=>$chat_id,
"text"=>"- تم نشر هذه الرساله 👇
-----------------------------------
$text
-----------------------------------
لعدد ($count) عضو. * 
",
'parse_mode'=>"html",
'disable_web_page_preview'=>true,
"message_id"=>$message_id+1,
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"حذف الرسالة",'callback_data'=>"delelink ".$msg]],
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"ethaa"]],
]])
]);
}
////////////توجية
if($data == "tawgih"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- أرسل رسالتك ليتم نشرها توجيه لجميع الأعضاء ↪️".
عدد الاعضاء :
'.$cmiim,
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- إلغاء ❌".' ,'callback_data'=>"ethaa"]],
]])
]);
file_put_contents("sudo/amr.txt","tawgih");
}
if($message and $amr == "tawgih" and in_array($from_id, $sudo)){
unlink("sudo/amr.txt");
bot('ForwardMessage',[
	'chat_id'=>$chat_id,
	'from_chat_id'=>$chat_id,
"message_id"=>$message_id+1,
]);

bot("sendMessage",[
"chat_id"=>$chat_id,
"text"=>"✅ جاري نشر رسالتك  لجميع الاعضاء  .",
]);
$msg = $message_id+1;
for($i=0;$i<count($miim);$i++){
$get =bot('ForwardMessage',[
	'chat_id'=>$miim[$i],
	'from_chat_id'=>$chat_id,
	'message_id'=>$message->message_id,
]);
$msg_id = $get->result->message_id;
file_put_contents("ms/$msg.txt",$miim[$i]."==". $msg_id."\n", FILE_APPEND);
$str= file_get_contents("sudo/mim.txt");
$str= str_replace($miim[$i]."\n","",$str);
file_put_contents("sudo/mim.txt",$str);
}
$ms=explode("\n",file_get_contents("ms/$msg.txt"));
$count= count($ms);
unlink("sudo/amr.txt");
bot("sendMessage",[
"chat_id"=>$chat_id,
"text"=>"تم نشر التوجية بنجاح 
لعدد ($count) عضو. * 
",
"message_id"=>$message_id+1,
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>"حذف الرسالة",'callback_data'=>"delelink ".$msg]],
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"ethaa"]],
]])
]);
}

if (preg_match('/^(delelink) (.*)/s',$data) ) {
  $data1 = explode(" ",$data);
  $mesg= $data1['1'];
  $getmes_id = explode("\n", file_get_contents("ms/$mesg.txt"));
  
bot('editmessagetext',[
'chat_id'=>$chat_id, 
'text'=>"جاري حذف رسالتك انتضر قليلا 🔎",
"message_id"=>$message_id,
]);

for($d=0;$d<count($getmes_id);$d++){
$ex = explode("==", $getmes_id[$d]);
$getmes_id1=$ex['1'];
$getids1=$ex['0'];
file_get_contents("https://api.telegram.org/bot$token/deleteMessage?chat_id=$getids1&message_id=$getmes_id1");
}
unlink("ms/$message_id.txt");
bot('editmessagetext',[
'chat_id'=>$chat_id, 
'text'=>"تم حذف رسالتك لدى كل الاعضاء ☑️",
"message_id"=>$message_id,
]);
}

///==== عدد آعضاء  ====\\\\

if($data == "memb"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- عدد مشتركين البوت هو '.$cuntei.' 👥".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
unlink("sudo/amr.txt");
}
$getben = explode("\n",file_get_contents("data/ban.txt"));
$countben = count($getben)-1;
if($data == 'ban'){
bot('answerCallbackQuery',[
'callback_query_id'=>$update->callback_query->id,
'message_id'=>$message_id,
'text'=>'عدد 💎 المحضورين ❌ : ' . $countben,
 'show_alert'=>true
 ]);      
}


if($data == "tnbeh"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- التنبيه عند دخول أحد للبوت 🚸".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- تفعيل التنبيه 🚸✅".' ,'callback_data'=>"tf3il"]],[['text'=>'- تعطيل التنبيه 🚸❎".' ,'callback_data'=>"tatil"]]
,[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]
])
]);
}

if($data == "tf3il"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم تفعيل تنبيه دخول الأعضاء 🚸✅".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
file_put_contents("sudo/tanbih.txt","yas");
}

if($data == "tatil"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم تعطيل تنبيه دخول الأعضاء 🚸❎".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
unlink("sudo/tanbih.txt");
}

/////////////////7////////////////
if($data == "estgbal"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- استقبال الرسائل من الأعضاء 🔃".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- تفعيل التواصل داخل البوت مع الاعضاء🔃✅".' ,'callback_data'=>"estgbalon"]],
[['text'=>'- تعطيل التواصل داخل البوت مع الاعضاء🔃❎".' ,'callback_data'=>"estgbaloff"]],
[['text'=>'مكان الاستقبال ".' ,'callback_data'=>"11111"]],
[['text'=>'الخاص ".' ,'callback_data'=>"typee"],
['text'=>'القروب ".' ,'callback_data'=>"supergruope"],
],
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]
])
]);
}

if($data == "typee"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم التفعيل سيتم ايصال الرسائل الى الخاص 🔃✅".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
file_put_contents("sudo/typee.txt","$from_id");
}


if($data == "supergruope"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'حسننا عزيزي الادمن قم بالذهاب الى قروب الاستقبال وارسل امر 
/setastgbal
📝".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- إلغاء ❌".' ,'callback_data'=>"ethaa"]],
]])
]);
file_put_contents("sudo/amr.txt","set");
}
if($text=="/setastgbal" and $amr == "set" and in_array($from_id, $sudo)){
file_put_contents("sudo/amr.txt","");
bot('sendmessage',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم تحديد هذا القروب ليكون قروبا للاستقبال ".',
]);
file_put_contents("sudo/typee.txt","$chat_id");
}
if($data == "estgbalon"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم تفعيل توجيه الرسائل 🔃✅".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
file_put_contents("sudo/estgbal.txt","on");
}

if($data == "estgbaloff"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'- تم تعطيل توجيه الرسائل 🔃❎".',
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- رجوع ↩️".' ,'callback_data'=>"admin"]],
]])
]);
unlink("sudo/amr.txt");
unlink("sudo/estgbal.txt");
}


if($data == 'atther'){

bot('editMessageText',[
'chat_id'=>$chat_id,
'message_id'=>$message_id,
'text'=>'⚙️هلاو مطور هذا القسم الخاص بل التعديل على المعلومات التي تضها في البوت',
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[
['text'=>'اضافت ترحيب 🗒','callback_data'=>'welc']],

[
['text'=>'اضافه رساله الرد','callback_data'=>'msrd']
],

[
['text'=>'رجوع الى الاوامر','callback_data'=>'admin']
]
]    
])
]);
}
if($data == 'welc'){
bot('editMessageText',[
'chat_id'=>$chat_id,
'message_id'=>$message_id,
'text'=>'ارسل الترحيب الان 🗒',
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>'الغاء ❌','callback_data'=>'atther']]    
]    
])
]);
file_put_contents("sudo/amr.txt","start");
}


if($message and $amr == "start" and in_array($from_id, $sudo)){
unlink("sudo/amr.txt");
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"تم حفظ الترحيب للاعضاء الجدد 
الترحيب هو : 
$text
",
]);
file_put_contents("data/start.txt","$text");
}








if($data == 'msrd'){
bot('editMessageText',[
'chat_id'=>$chat_id,
'message_id'=>$message_id,
'text'=>"قم بتحديد رسالة الرد على العضو بعد ان يقوم بارسال رساله لك ....
",
'reply_markup'=>json_encode([
'inline_keyboard'=>[
[['text'=>'الغاء ❌','callback_data'=>'atther']]    
]    
])
]);

file_put_contents("sudo/amr.txt","msrd");
}

if($message and $amr == "msrd" and in_array($from_id, $sudo)){
unlink("sudo/amr.txt");
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"تم حفظ رسالة الرد 
رسالة الرد هي  : 
$text
",
]);

file_put_contents("data/msrd.txt","$text");
}





$yppee=file_get_contents("sudo/typee.txt");
if($yppee==null or $yppee==""){
$yppee=$wathq1;

}
$get_ban=file_get_contents('data/ban.txt');
$ban =explode("\n",$get_ban);

if($text=="ترقية" and in_array($from_id,$sudo)
){

$rand=rand(111111,999999);
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"اهلا عزيزي المطور لرفع اي شخص ليكون ادمن قم بارسال هذا الرمز له 
رمز الترقية : `$rand`
",
'reply_to_message_id'=>$message_id
,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
]);
file_put_contents("data/trgih.txt","$rand");
}
$adminall=explode("\n",file_get_contents("sudo/admin.txt"));
$amrtr=file_get_contents("data/$from_id.txt");
if($text=="ارفعني" and $from_id!=$wathq1 and !in_array($from_id, $sudo) ){
if(!in_array($from_id, $ban)){
if(!in_array($from_id, $adminall)){
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"اهلا بك عزيزي 
اذا كنت تريد ان يقوم البوت برفعك ادمن قم بارسال رمز الترقيه المكون من 6 ارقام 
",
'reply_to_message_id'=>$message_id
,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
]);
file_put_contents("data/$from_id.txt","yes");
}else{
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"لقد تمت ترقيتك بالفعل مسبقا   ✅
",
'reply_to_message_id'=>$message_id
,
]);
}
}else{
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"❌ المعذرة لا استطيع ترقيتك لانك محظور من قبل مالك البوت 
",
'reply_to_message_id'=>$message_id
,
]);
}
}


$randtrg=file_get_contents("data/trgih.txt");
if($text and !$data and $amrtr == "yes" ){
unlink("data/$from_id.txt");


if($text==$randtrg){

if(!in_array($from_id, $adminall)){
file_put_contents("sudo/admin.txt","$from_id\n",FILE_APPEND);
}
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"لقد تمت ترقيتك بنجاح عزيزي ✅
",
]);
bot('sendmessage',[
	'chat_id'=>$yppee,
'text'=>"✅  
 لقد تمت ترقية  العضو  
 - [$name](tg://user?id=$from_id) 
",
]);
}else{
bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"عذرا عزيزي رمز الترقية خاطئ❌",
]);
}
}
if($text=="الادمنية" and $from_id == $wathq1 
){
unlink("sudo/admins.txt");
for($h=0;$h<count($adminall);$h++){
if($adminall[$h] != ""){
$admin = json_decode(file_get_contents("http://api.telegram.org/bot$token/getChat?chat_id=$adminall[$h]"))->result;
$from=$adminall[$h];
$name= $admin->first_name;

$admins="- [$name](tg://user?id=$from) `$from`";
file_put_contents("sudo/admins.txt","$admins\n",FILE_APPEND);

}}

$admins=file_get_contents("sudo/admins.txt");


bot('sendmessage',[
	'chat_id'=>$chat_id,
'text'=>"ℹ هذة هي قائمة الادمنية 
$admins
",
'reply_to_message_id'=>$message_id
,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
]);

}
if (preg_match('/^(تنزيل) (.*)/s',$text) and $from_id == $wathq1 
) 
{
$textt = str_replace("تنزيل ","",$text);

$strlen=strlen($textt);
if($strlen < 12){

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>' تم ✅ تنزيل العضو من الادمنية ❌',
'reply_to_message_id'=>$message_id
]);

bot('sendMessage',[
'chat_id'=>$textt,
'text'=>'تم ✅  تنزيلك من الا دمنية ❌'
]);
$bin=file_get_contents('sudo/admin.txt');
$str = str_replace($textt."\n", '' ,$bin);

file_put_contents('sudo/admin.txt', $str);

}
}



///====  الاعضاء  ====\\\\
$start= file_get_contents("data/start.txt");
$ainfo= file_get_contents("data/ainfo.txt");
$chan= file_get_contents("data/chan.txt");
$law= file_get_contents("data/law.txt");
$infobot= file_get_contents("data/infobot.txt");
$msrd= file_get_contents("data/msrd.txt");



if($text == '/start' and !in_array($from_id,$ban) and $message->chat->type == 'private' and $chat_id != $sudo ){
$user = $update->message->from->username;
if($user){
bot('sendphoto',[
'chat_id'=>$chat_id,
'photo'=>"https://t.me/bvvvca/3", #رابط صوره البداء
'caption'=>"*
◼ مرحبا بك في بوت التواصل ارسل رسالتك وانتظر الرد 🧛 .

𖤍 ارسل ماتريد ارسالة الان .

◼ لإستخراج الايدي الخاص بك ارسل  /id . 

*",
'reply_markup'=>json_encode([
'inline_keyboard'=>[[['text'=>"قناة المطور 𖤍","url"=>"t.me/nnnb50"]]
]
])
]);
}else{
bot('sendmessage',[
'chat_id'=>$chat_id,
'text'=>"*
◼ مرحبا بك في بوت التواصل ارسل رسالتك وانتظر الرد 🧛 .

𖤍 ارسل ماتريد ارسالة الان .

◼ لإستخراج الايدي الخاص بك ارسل  /id . 

*",
'reply_markup'=>json_encode([
'inline_keyboard'=>[[['text'=>"قناة المطور 𖤍","url"=>"t.me/nnnb50"]]
]
])
]);
}
}








$yppee=file_get_contents("sudo/typee.txt");
if($yppee==null or $yppee==""){
$yppee=$wathq1;

}

$co_m_all=file_get_contents("count/user/all.txt");
$co1=$co_m_all+1;



$repp=$message->reply_to_message->message_id-1;
$msg=explode("=",file_get_contents("message/$repp.txt"));

$get_ban=file_get_contents('data/ban.txt');
$get_ban=file_get_contents('data/ban.txt');
$ban =explode("\n",$get_ban);
if($text){

if($text != '/start' and $text != 'جهة اتصال المدير☎️' and $text != '⚜️〽️┇قناه البوت' and $text != 'ارفعني' and $text != 'القوانين ⚠️' and $text != 'معلومات المدير 📋' and   $text !='المساعده 💡' and $text !='اطلب بوتك من المطور' and $message->chat->type == 'private' and $from_id != $wathq1 ){
if(!in_array($from_id, $ban)){
if($estgbal=="on" or $estgbal==null){
bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,

]);

$get= bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id,

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");


file_put_contents("count/user/all.txt","$co1");


if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd ــــ ",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"*
تم ارسال الرسالة سأقوم بالرد باقرب وقت ان شاء الله 🌸

*",
'reply_markup'=>json_encode([
'inline_keyboard'=>[[['text'=>"قناة المطور 𖤍","url"=>"t.me/nnnb50"]]
]
])
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"❌ المعذرة لا تستطيع ارسال الرسائل انت محظور ",
'reply_to_message_id'=>$message_id
]);
}
}}


$photo=$message->photo;
$video=$message->video;
$document=$message->document;
$sticker=$message->sticker;
$voice=$message->voice;
$audio=$message->audio;

$n_id =$msg['1'];
if($reply and $text != 'الغاء الحظر' and $text != 'حظر' and $text != 'معلومات' and $chat_id == $yppee  
and $n_id!= null){
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

if($text){
$get=bot('sendMessage',[
'chat_id'=>$msg['0'],
'text'=>$text,    
'reply_to_message_id'=>$msg['2'],

]);
$msg_id = $get->result->message_id;
}else{

if($photo){
$sens="sendphoto";
$file_id = $update->message->photo[1]->file_id;
}
if($document){
$sens="senddocument";
$file_id = $update->message->document->file_id;
}
if($video){
$sens="sendvideo";
$file_id = $update->message->video->file_id;
}

if($audio){
$sens="sendaudio";
$file_id = $update->message->audio->file_id;
}

if($voice){
$sens="sendvoice";
$file_id = $update->message->voice->file_id;
}

if($sticker){
$sens="sendsticker";
$file_id = $update->message->sticker->file_id;
}

$ss=str_replace("send","",$sens);
$get1=bot($sens,[
"chat_id"=>$msg['0'],
"$ss"=>"$file_id",
'caption'=>"$getfull",
'reply_to_message_id'=>$msg['2'],
]);

$msg_id = $get->result->message_id;
}

$ch_id =$msg['0'];
$name_id =$msg['1'];
$wathqid="$ch_id=$msg_id=$name_id";
file_put_contents("message/$msg_id.txt","$wathqid");

$co_m_ad=file_get_contents("count/admin/$ch_id.txt");
$co=$co_m_ad+1;
file_put_contents("count/admin/$ch_id.txt","$co");

$co_m_all=file_get_contents("count/admin/all.txt");
$coo=$co_m_all+1;
file_put_contents("count/admin/all.txt","$coo");
bot('sendmessage',[
'chat_id'=>$yppee,
'text'=>"
◾ تم الارسال لـ [$name_id](tg://user?id=$ch_id) بنجاح .
",
'reply_to_message_id'=>$message_id
,'parse_mode'=>"MarkDown",

'disable_web_page_preview'=>true,
'reply_markup'=>json_encode([ 
'inline_keyboard'=>[
[['text'=>"◾ تعديل الرسالة .",'callback_data'=>"edit_msg ".$msg_id],
['text'=>"◾ حذف الرسالة .",'callback_data'=>"del_msg ".$msg_id]],
]
])
]);
}}

if($text == "/id"){
$username = $message->from->username;
$photo = "http://telegram.me/$username";
bot( SendPhoto ,[
 chat_id =>$chat_id,
 photo =>$photo,
 caption =>"
👤┇اسمك~> $name
🆔┇ايديك~> $from_id
",
]);
}

if (preg_match('/^(del_msg) (.*)/s',$data) ) {
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

  $data1 = explode(" ",$data);
  $wathqid= $data1['1'];
$info=explode("=",file_get_contents("message/$wathqid.txt"));

  $ch_id= $info['0'];
  $msg_id= $info['1'];
  $name_id =$info['2'];
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>"
◾ تم حذف الرسالة لـ [$name_id](tg://user?id=$ch_id) بنجاح

",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
]);
bot('deleteMessage',[
'chat_id'=>$ch_id,
'message_id'=>$msg_id,
]);
  }
}
if (preg_match('/^(edit_msg) (.*)/s',$data) ) {
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

$data1 = explode(" ",$data);
  $wathqid= $data1['1'];
$info=explode("=",file_get_contents("message/$wathqid.txt"));

  $ch_id= $info['0'];
  $msg_id= $info['1'];
  $name_id =$info['2'];
  file_put_contents("data/t3dil.txt","$ch_id=$msg_id=$name_id");
bot('sendmessage',[
'chat_id'=>$chat_id,
'text'=>"
◾ قم بارسال رسالتك الجديده ليتم تعديل الرسالة السابقه لدى [$name_id](tg://user?id=$ch_id)  .
",
'reply_to_message_id'=>$message_id
,'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
 'reply_markup'=>json_encode([ 
      'inline_keyboard'=>[
[['text'=>'- إلغاء ❌".' ,'callback_data'=>"trag3"]],
]])
]);
file_put_contents("sudo/amr.txt","edit");
  }
}
if($data == "trag3"){
bot('EditMessageText',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>'تم الغاء التعديل بنجاح".',
]);
file_put_contents("sudo/amr.txt","");
file_put_contents("data/t3dil.txt","");
}
if($text and $amr == "edit" and $chat_id== $yppee){
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

file_put_contents("sudo/amr.txt","");
$wathqget=file_get_contents("data/t3dil.txt");

  $wathqidd = explode("=",$wathqget);
  $ch_id= $wathqidd['0'];
  $msg_id= $wathqidd['1'];
  $name_id =$wathqidd['2'];
  bot('deleteMessage',[
'chat_id'=>$chat_id,
'message_id'=>$message_id-2,
]);
bot('deleteMessage',[
'chat_id'=>$chat_id,
'message_id'=>$message_id-1,
]);

bot('sendmessage',[
    'chat_id'=>$chat_id,
    'message_id'=>$message_id,
'text'=>"- ✅ تم التعديل الرسالة لـ [$name_id](tg://user?id=$ch_id) بنجاح .",
'reply_to_message_id'=>$message_id
,'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_markup'=>json_encode([ 
'inline_keyboard'=>[
[['text'=>"◾ تعديل الرسالة .",'callback_data'=>"edit_msg ".$msg_id],
['text'=>"◾ حذف الرسالة .",'callback_data'=>"del_msg ".$msg_id]],
]
])
]);
file_put_contents("data/t3dil.txt","");
bot('EditMessageText',[
    'chat_id'=>$ch_id,
    'message_id'=>$msg_id,
    'text'=>
$text,
]);
}}

if (preg_match('/^(حظر) (.*)/s',$text) and $chat_id == $yppee ) {
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

$textt = str_replace("حظر ","",$text);
$textt = str_replace(" ","",$text);
$strlen=strlen($textt);
if($strlen < 10){
if(!in_array($textt, $ban)){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>'تم ✅ حضر العضو 🚹',
'reply_to_message_id'=>$message_id
]);

bot('sendMessage',[
'chat_id'=>$textt,
'text'=>'تم ✅ حضرك من البوت ❌',
]);
file_put_contents('data/ban.txt', $textt. "\n", FILE_APPEND);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>' العضو محظور مسبقا🚫 🚹',
'reply_to_message_id'=>$message_id
]);
}
}}
}
if (preg_match('/^(الغاء حظر) (.*)/s',$text) and $chat_id == $yppee ) {
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

$textt = str_replace("الغاء حظر ","",$text);
$textt = str_replace(" ","",$text);
$strlen=strlen($textt);
if($strlen < 10){
if(in_array($textt, $ban)){

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>'تم ✅ الغاء حضر العضو ❌',
'reply_to_message_id'=>$message_id
]);

bot('sendMessage',[
'chat_id'=>$textt,
'text'=>'تم ✅ الغاء حضرك ❌'
]);
$bin=file_get_contents('data/ban.txt');
$str = str_replace($textt."\n", '' ,$bin);

file_put_contents('data/ban.txt', $str);

}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>' 🚫 العضو ليس محظور 🚹',
'reply_to_message_id'=>$message_id
]);
}}}
}



if($reply and $text == 'حظر' and $chat_id == $yppee  and $n_id!= null){
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

//$from = $message->reply_to_message->forward_from->id;
$from = $msg['0'];
if(!in_array($from, $ban)){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>'تم ✅ حضر العضو 🚹',
'reply_to_message_id'=>$message_id
]);

bot('sendMessage',[
'chat_id'=>$from,
'text'=>'تم ✅ حضرك من البوت ❌',
]);

file_put_contents('data/ban.txt', $from. "\n", FILE_APPEND);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>' العضو محظور مسبقا🚫 🚹',
'reply_to_message_id'=>$message_id
]);
}}
}

if($reply and $text == 'الغاء الحظر' and $chat_id == $yppee and $n_id!= null){
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

//$from = $message->reply_to_message->forward_from->id;
$from = $msg['0'];
if(in_array($from, $ban)){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>'تم ✅ الغاء حضر العضو ❌',
'reply_to_message_id'=>$message_id
]);

bot('sendMessage',[
'chat_id'=>$from,
'text'=>'تم ✅ الغاء حضرك ❌'
]);

$bin=file_get_contents('data/ban.txt');
$str = str_replace($from ."\n", '' ,$bin);

file_put_contents('data/ban.txt', $str);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>' 🚫 العضو ليس محظور 🚹',
'reply_to_message_id'=>$message_id,
]);
}
}
}
//معلومات الاعضاء 
if($reply and $text == 'معلومات' and $chat_id == $yppee){
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

//$from = $message->reply_to_message->forward_from->id;
$from = $msg['0'];

$admin = json_decode(file_get_contents("http://api.telegram.org/bot$token/getChat?chat_id=$from"))->result;

$name= $admin->first_name;

$user= $admin->username;

if(!in_array($from, $ban)){

$info="✅ متفاعل";
}else{
$info="🚫 محظور";
}
$co_m_us=file_get_contents("count/user/$from.txt");
$co_m_ad=file_get_contents("count/admin/$from.txt");

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"ℹ معلومات العضو 
~~~~~~~~~~~~~~~~~~~~~~~
- الاسم : [ $name](tg://user?id=$from)  .
- الايدي : `$from`
- المعرف : *@$user*
- حالة العضو : $info
- عدد الرسائل المستلمة منة : $co_m_us ✉
- عدد الرسائل المرسلة لة : $co_m_ad 📬

",
'reply_to_message_id'=>$message_id,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
]);
}
}
if( $text == 'معلومات' and !$reply  and $chat_id == $yppee){
if( in_array($from_id,$sudo)
or in_array($from_id, $adminall)){

unlink("sudo/admins.txt");
for($h=0;$h<count($adminall);$h++){
if($adminall[$h] != ""){
$admin = json_decode(file_get_contents("http://api.telegram.org/bot$token/getChat?chat_id=$adminall[$h]"))->result;
$from=$adminall[$h];
$name= $admin->first_name;
$c= $h+1;
$admins="$c - [$name](tg://user?id=$from) `$from`";
file_put_contents("sudo/admins.txt","$admins\n",FILE_APPEND);

}}

$admins=file_get_contents("sudo/admins.txt");


$co_m_us=file_get_contents("count/user/all.txt");
$co_m_ad=file_get_contents("count/admin/all.txt");
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"ℹ معلومات شاملة عن البوت  
~~~~~~~~~~~~~~~~~~~~~~~
👮 - الادمنية : 
$admins
--------------------
👪 - عدد الاعضاء : $cuntei
🚫 - المحضورين : $countben
--------------------
📮 - الرسائل 
📩 - المستلمة :$co_m_us
📬 - الصادرة :$co_m_ad


",
'reply_to_message_id'=>$message_id,
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
]);
}
}
$photo=$message->photo;
$video=$message->video;
$document=$message->document;
$sticker=$message->sticker;
$voice=$message->voice;
$audio=$message->audio;
$forward =$message->forward_from_chat;
$c_photo=file_get_contents("data/photo.txt");
$c_video=file_get_contents("data/video.txt");
$c_document=file_get_contents("data/document.txt");
$c_sticker=file_get_contents("data/sticker.txt");
$c_voice=file_get_contents("data/voice.txt");
$c_audio=file_get_contents("data/audio.txt");
$c_forward =file_get_contents("data/audio.txt");
if($from_id!=$wathq1 and $message->chat->type == 'private' ){
//الصور
if($photo and ! $forward){
if($c_photo=="❌"or $c_photo== null){
if($estgbal=="on" or $estgbal==null){

bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
]);

$get=bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");

file_put_contents("count/user/all.txt","$co1");

if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd..",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ارسال الرسالة ساقوم بالرد باقرب وقت إن شاء الله 🌸",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"عذرا استقبال الصور مغلق ❌",
'reply_to_message_id'=>$message_id
]);
}

}
//الفيديو
if($video and ! $forward ){
if($c_video=="❌"or $c_photo== null){
if($estgbal=="on" or $estgbal==null){
bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
]);
$get=bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");
file_put_contents("count/user/all.txt","$co1");


if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ارسال الرسالة ساقوم بالرد باقرب وقت ان شاء الله 🌸",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"عذرا استقبال الفيديو مغلق ❌",
'reply_to_message_id'=>$message_id
]);
}

}

//الملفات
if($document and ! $forward){
if($c_document=="❌"or $c_photo== null){
if($estgbal=="on" or $estgbal==null){
bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
]);
$get=bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");
file_put_contents("count/user/all.txt","$co1");

if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ارسال الرسالة ساقوم بالرد باقرب وقت ان شاء الله 🌸",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"عذرا استقبال الملفات مغلق ❌",
'reply_to_message_id'=>$message_id
]);
}

}

//الملصقات
if($sticker and ! $forward ){
if($c_sticker=="❌"or $c_photo== null){
if($estgbal=="on" or $estgbal==null){
bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
]);
$get=bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");
file_put_contents("count/user/all.txt","$co1");

if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ارسال الرسالة ساقوم بالرد باقرب وقت ان شاء الله 🌸",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"عذرا استقبال الملفات مغلق ❌",
'reply_to_message_id'=>$message_id
]);
}

}

//الصوتيات
if($voice and ! $forward ){
if($c_voice=="❌"or $c_photo== null){
if($estgbal=="on" or $estgbal==null){
bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
]);
$get=bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");
file_put_contents("count/user/all.txt","$co1");

if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ارسال الرسالة ساقوم بالرد باقرب وقت ان شاء الله 🌸",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"عذرا استقبال الصوتيات مغلق ❌",
'reply_to_message_id'=>$message_id
]);
}

}
//الصوتيات
if($audio and ! $forward ){
if($c_audio=="❌"or $c_photo== null){
if($estgbal=="on" or $estgbal==null){
bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
]);
$get=bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");
file_put_contents("count/user/all.txt","$co1");

if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ارسال الرسالة ساقوم بالرد باقرب وقت ان شاء الله 🌸",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"عذرا استقبال الموسيقى مغلق ❌",
'reply_to_message_id'=>$message_id
]);
}

}
//التوجية
if($forward ){
if($c_forward=="❌"or $c_forward== null){
if($estgbal=="on" or $estgbal==null){
bot('sendMessage',[
'chat_id'=>$yppee,
'text'=>"رساله من : [$name](tg://user?id=$from_id)
",
'parse_mode'=>"MarkDown",
'disable_web_page_preview'=>true,
'reply_to_message_id'=>$message->reply_to_message->message_id-1,
]);
$get=bot('forwardMessage',[
'chat_id'=>$yppee,
'from_chat_id'=>$chat_id,
'message_id'=>$message_id

]);
$msg_id = $get->result->message_id-1;

$from_id_name="$chat_id=$name=$message_id";
file_put_contents("message/$msg_id.txt","$from_id_name");

$co_m_us=file_get_contents("count/user/$from_id.txt");
$co=$co_m_us+1;
file_put_contents("count/user/$from_id.txt","$co");
file_put_contents("count/user/all.txt","$co1");

if($msrd !=null){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"$msrd",
'reply_to_message_id'=>$message_id
]);
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ارسال الرسالة ساقوم بالرد باقرب وقت ان شاء الله 🌸",
'reply_to_message_id'=>$message_id
]);
}
}else{
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"تم ايقاف استقبال الرسائل من قبل مالك البوت ",
'reply_to_message_id'=>$message_id
]);
}
}else{

bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"عذرا استقبال التوجية مغلق ❌",
'reply_to_message_id'=>$message_id
]);
}

}
}


if(strstr($text,"t.me") == true or strstr($text,"telegram.me") == true or strstr($text,"https://") == true or strstr($text,"://") == true or strstr($text,"wWw.") == true or strstr($text,"WwW.") == true or strstr($text,"T.me/") == true or strstr($text,"WWW.") == true or strstr($caption,"t.me") == true or strstr($caption,"telegram.me")) {   
if($users == "مقفول"){
	    bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ يمنع ارسال الروابط .",
        ]);
}
}

if($data == "hmaih"){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"
تحكم بحماية وقفل الوسائط المتعدده

❌ =  مفتوح 
✅ = مقفل 

لقفل الوسائط ارسل امر 
قفل ( الصور - الفيديو - الملفات - التوجيه - الصوت - الموسيقى - الروابط - المعرفات ) 
مثال قفل التوجية
او 
فتح التوجية

قفل الكل : لقفل جميع الوسائط 
فتح الكل : لفتح جميع الوسائط 
-----------------------",
'reply_to_message_id'=>$message->message_id,
'reply_markup'=>json_encode([ 
'inline_keyboard'=>[
[['text'=>" حالة الحماية  ",'callback_data'=>"halh"]],
]
])
]);
}
$c_photo=file_get_contents("data/photo.txt");
$c_video=file_get_contents("data/video.txt");
$c_document=file_get_contents("data/document.txt");
$c_sticker=file_get_contents("data/sticker.txt");
$c_voice=file_get_contents("data/voice.txt");
$c_audio=file_get_contents("data/audio.txt");
$c_forward =file_get_contents("data/audio.txt");

if($text=="قفل الصور" and in_array($from_id,$sudo)){
file_put_contents("data/photo.txt","✅");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم قفل الصور .",
        ]);
}

if($text=="فتح الصور" and in_array($from_id,$sudo)){
file_put_contents("data/photo.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم فتح الصور .",
        ]);
}
if($text=="قفل الفيديو" and in_array($from_id,$sudo)){
file_put_contents("data/video.txt","✅");

bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم قفل الفيديو .",
        ]);
}
if($text=="فتح الفيديو" and in_array($from_id,$sudo)){
file_put_contents("data/video.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم فتح الفيديو .",
        ]);
}

if($text=="قفل الملفات" and in_array($from_id,$sudo)){
file_put_contents("data/document.txt","✅");

bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم  $text .",
        ]);
}
if($text=="فتح الملفات" and in_array($from_id,$sudo)){
file_put_contents("data/document.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم $text .",
        ]);
}

if($text=="قفل الملصقات" and in_array($from_id,$sudo)){
file_put_contents("data/sticker.txt","✅");

bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم  $text .",
        ]);
}
if($text=="فتح الملصقات" and in_array($from_id,$sudo)){
file_put_contents("data/sticker.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم $text .",
        ]);
}

if($text=="قفل الصوتيات" and in_array($from_id,$sudo)){
file_put_contents("data/voice.txt","✅");

bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم  $text .",
        ]);
}
if($text=="فتح الصوتيات" and in_array($from_id,$sudo)){
file_put_contents("data/voice.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم $text .",
        ]);
}


if($text=="قفل الموسيقى" and in_array($from_id,$sudo)){
file_put_contents("data/audio.txt","✅");

bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم  $text .",
        ]);
}
if($text=="فتح الموسيقى" and in_array($from_id,$sudo)){
file_put_contents("data/audio.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم $text .",
        ]);
}
if($text=="قفل التوجية" and in_array($from_id,$sudo)){
file_put_contents("data/forward.txt","✅");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم  $text .",
        ]);
}
if($text=="فتح التوجية" and in_array($from_id,$sudo)){
file_put_contents("data/forward.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم $text .",
        ]);
}

if($text=="قفل الكل" and in_array($from_id,$sudo)){
file_put_contents("data/forward.txt","✅");
file_put_contents("data/audio.txt","✅");
file_put_contents("data/voice.txt","✅");
file_put_contents("data/sticker.txt","✅");
file_put_contents("data/document.txt","✅");
file_put_contents("data/video.txt","✅");
file_put_contents("data/photo.txt","✅");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم  $text .",
        ]);
}
if($text=="فتح الكل" and in_array($from_id,$sudo)){
file_put_contents("data/forward.txt","❌");
file_put_contents("data/audio.txt","❌");
file_put_contents("data/voice.txt","❌");
file_put_contents("data/sticker.txt","❌");
file_put_contents("data/document.txt","❌");
file_put_contents("data/video.txt","❌");
file_put_contents("data/photo.txt","❌");
bot('sendmessage',[
       'chat_id'=>$chat_id,
        'text'=>"◾ تم  $text .",
        ]);
}


$c_photo=file_get_contents("data/photo.txt");
$c_video=file_get_contents("data/video.txt");
$c_document=file_get_contents("data/document.txt");
$c_sticker=file_get_contents("data/sticker.txt");
$c_voice=file_get_contents("data/voice.txt");
$c_audio=file_get_contents("data/audio.txt");
$c_forward =file_get_contents("data/audio.txt");

if($data == "halh"){
bot('sendMessage',[
'chat_id'=>$chat_id,
'text'=>"
تحكم بحماية وقفل الوسائط المتعدده

❌ =  مفتوح 
✅ = مقفل 

⭕ الحالة /
▫الصور : $c_photo
▫الفيديو : $c_video
▫الملفات : $c_document
▫الملصقات : $c_sticker
▫ الصوتيات : $c_voice
▫الموسيقى : $c_audio
▫التوجية : $c_forward
▫الراوبط : 

-----------------------",
'reply_to_message_id'=>$message->message_id,
]);
}

#كود النسخ الاحتياطي للمطور : سعيد 

function SAIEDZip($SAIEDZip1, $SAIEDZip2){
$SAIEDZip4 = realpath($SAIEDZip1);
$SAIEDZip = new ZipArchive();
$SAIEDZip->open($SAIEDZip2, ZipArchive::CREATE | ZipArchive::OVERWRITE);
$SAIEDZip3 = new RecursiveIteratorIterator(
new RecursiveDirectoryIterator($SAIEDZip4),
RecursiveIteratorIterator::LEAVES_ONLY);
foreach($SAIEDZip3 as $SAIEDZip5 => $SAIEDZip6){
if(!$SAIEDZip6->isDir()){
$SAIEDZip7 = $SAIEDZip6->getRealPath();
$SAIEDZip8 = substr($SAIEDZip7, strlen($SAIEDZip4) + 1);
$SAIEDZip->addFile($SAIEDZip7, $SAIEDZip8);
}}
$SAIEDZip->close();
}
# كود حجم الملف لـ @MrDGSY #
function SAIEDZip1($SAIEDZip9, $SAIEDZip10 = 2){
$SAIEDZip11=array(' B', ' KB', ' MB', ' GB', ' TB', ' PB', ' EB', ' ZB', ' YB');
$SAIEDZip12=floor((strlen($SAIEDZip9) - 1) / 3);
return sprintf("%.{$SAIEDZip10}f", $SAIEDZip9 / pow(1024, $SAIEDZip12)) . @$SAIEDZip11[$SAIEDZip12];
}
$SAIEDZip15 = json_decode(file_get_contents('php://input'));
$SAIEDZip16 = $SAIEDZip15->message;
$SAIEDZip17 = $SAIEDZip16->text;
$SAIEDZip18 = $SAIEDZip16->message_id;
if($SAIEDZip17 == "نسخة إحتياطية"){
$SAIEDZip14 = "saied.tk"; //دومين استضافتك
$RSAIED = "ايديك"; //ايديك
date_default_timezone_set("Asia/Damascus");
$SAIEDZip13 = date("{h-i-s}");
SAIEDZip('./', "Backup-$SAIEDZip13.zip");

bot('senddocument',[
'chat_id'=>$RSAIED,
'document'=>new CURLFile("Backup-$SAIEDZip13.zip"),
'caption'=>"Backup. 📦
Today's date : ".date('Y/m/d')." 📆
The Time is : ".date('h:i A')." ⏰
File size : ".SAIEDZip1(filesize("Backup-$SAIEDZip13.zip"))." 🏷",

]);
unlink("Backup-$SAIEDZip13.zip");
}





