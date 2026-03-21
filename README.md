
I  build a projects for user friendly 
and it is a cirtificate genretor 
Here code is 🔥
<!DOCTYPE html><html lang="en">
<head>
<meta charset="UTF-8">
<title>Realistic Certificate Generator</title>
<script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>
<style>
body { font-family: Georgia, serif; background:#eef2f5; text-align:center; }
.container { background:#fff; padding:20px; width:400px; margin:30px auto; border-radius:10px; }
input,select { width:90%; padding:10px; margin:8px; }
button { padding:10px 18px; background:#111; color:#fff; border:none; cursor:pointer; }
.error { border:2px solid red; }#certificate { display:none; width:1000px; margin:40px auto; padding:90px 70px; background:#fff url('https://www.transparenttextures.com/patterns/cream-paper.png'); border:2px solid #cfcfcf; position:relative; box-shadow:0 10px 25px rgba(0,0,0,0.15); } #certificate::before{ content:""; position:absolute; top:15px; left:15px; right:15px; bottom:15px; border:1px solid #ddd; }

.watermark{ position:absolute; top:50%; left:50%; transform:translate(-50%,-50%); opacity:0.05; width:350px; }

.logo img{ width:130px; position:absolute; top:30px; left:40px; }

.meta{ position:absolute; top:30px; right:50px; font-size:14px; }

.title{ font-size:40px; letter-spacing:3px; } .name{ font-size:34px; margin:25px 0; } .desc{ width:70%; margin:25px auto; line-height:1.8; }

.seal{ position:absolute; bottom:60px; right:70px; width:90px; height:90px; border-radius:50%; border:2px solid #caa74d; display:flex; align-items:center; justify-content:center; transform:rotate(-15deg); font-size:11px; color:#caa74d; }

.footer{ margin-top:90px; display:flex; justify-content:space-between; } .line{ border-top:1px solid #000; width:160px; margin-top:5px; } </style>

</head><body><div class="container">
<h2>🎓 Generate Certificate</h2>
<input type="text" id="name" placeholder="Enter Full Name"><select id="field">
<option value="">Select Course</option>
<option>Data Structures & Algorithms</option>
<option>Full Stack Web Development</option>
<option>AI & Machine Learning</option>
<option>Cloud Computing & DevOps</option>
<option>Cyber Security</option>
<option>Blockchain Development</option>
<option>Hackathon Participation</option>
<option>Hackathon Winner</option>
</select><select id="type">
<option value="">Certificate Type</option>
<option>Internship Completion</option>
<option>Professional Certification</option>
<option>Training Program</option>
<option>Bootcamp Completion</option>
<option>Hackathon Certificate</option>
</select><select id="company">
<option value="">Company</option>
<option value="google">Google</option>
<option value="microsoft">Microsoft</option>
<option value="amazon">Amazon</option>
<option value="meta">Meta</option>
<option value="flipkart">Flipkart</option>
<option value="apple">Apple</option>
</select><select id="exp">
<option value="">Experience</option>
<option>No Experience</option>
<option>0-6 Months</option>
<option>1-2 Years</option>
<option>2+ Years</option>
</select><button onclick="generate()">Generate</button> <button onclick="download()">Download</button>

</div><div id="certificate">
<img class="watermark" id="watermark">
<div class="logo"><img id="logo"></div>
<div class="meta" id="meta"></div><div class="title" id="title"></div>
<p>This is to certify that</p>
<div class="name" id="username"></div>
<p id="expLine"></p><div class="desc" id="desc"></div><div class="seal">CERTIFIED</div><div class="footer">
<div>
<img id="sign1" width="130">
<div class="line"></div>
<p>Authorized Signature</p>
</div>
<div>
<img id="sign2" width="130">
<div class="line"></div>
<p>Program Director</p>
</div>
</div>
</div><script>

let logos={
 google:"https://logo.clearbit.com/google.com",
 microsoft:"https://logo.clearbit.com/microsoft.com",
 amazon:"https://logo.clearbit.com/amazon.com",
 meta:"https://logo.clearbit.com/meta.com",
 flipkart:"https://logo.clearbit.com/flipkart.com",
 apple:"https://logo.clearbit.com/apple.com"
};

let signatures=[
 "https://dummyimage.com/150x50/000/fff&text=Sign+A",
 "https://dummyimage.com/150x50/000/fff&text=Sign+B",
 "https://dummyimage.com/150x50/000/fff&text=Sign+C",
 "https://dummyimage.com/150x50/000/fff&text=Sign+D"
];

function generate(){
 let name=document.getElementById("name");
 let field=document.getElementById("field");
 let type=document.getElementById("type");
 let company=document.getElementById("company");
 let exp=document.getElementById("exp");

 [name,field,type,company,exp].forEach(e=>e.classList.remove("error"));

 if(!name.value){name.classList.add("error");return;}
 if(!field.value){field.classList.add("error");return;}
 if(!type.value){type.classList.add("error");return;}
 if(!company.value){company.classList.add("error");return;}
 if(!exp.value){exp.classList.add("error");return;}

 document.getElementById("logo").src=logos[company.value];
 document.getElementById("watermark").src=logos[company.value];

 // RANDOM SIGNATURE
 document.getElementById("sign1").src=signatures[Math.floor(Math.random()*signatures.length)];
 document.getElementById("sign2").src=signatures[Math.floor(Math.random()*signatures.length)];

 let borders=["#999","#222","#0d47a1","#4caf50","#9c27b0"];
 document.getElementById("certificate").style.border="2px solid "+borders[Math.floor(Math.random()*borders.length)];

 document.getElementById("title").innerText=type.value;
 document.getElementById("username").innerText=name.value;
 document.getElementById("expLine").innerText=(exp.value==="No Experience")?"":"Experience: "+exp.value;

 document.getElementById("desc").innerText=
 "has successfully completed the "+field.value+" program, demonstrating exceptional technical knowledge, strong analytical thinking, problem-solving ability, teamwork, leadership skills, and a commitment to professional excellence in real-world industry environments.";

 let id="CERT-"+Math.floor(Math.random()*1000000);
 let date=new Date().toLocaleDateString();
 document.getElementById("meta").innerText=id+" | "+date;

 document.getElementById("certificate").style.display="block";
}

function download(){
 html2canvas(document.getElementById("certificate"),{
  useCORS:true,
  allowTaint:true,
  backgroundColor:"#ffffff"
 }).then(canvas=>{
  let link=document.createElement("a");
  link.download="certificate.png";
  link.href=canvas.toDataURL();
  link.click();
 });
}

</script></body>
</html>