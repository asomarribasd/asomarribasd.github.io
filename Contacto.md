---
layout: page
excerpt: "Contacta a Ahmed"
title: "Contacto"
permalink: /contacto/
---

<script>
$(document).ready(function(){

	
	
	$("#sendForm").submit(function(e) {
	
	var $contactForm = $("#sendForm");
	
	inputName = $("#sendForm input[name=name]"),
    inputEmail = $('#sendForm input[name=email]'),
    inputPhone = $('#sendForm input[name=phone]'),
    textAreaMessage = $("#sendForm textarea[name=message]");
    
	var messageData = {message: textAreaMessage.val(),
				name: inputName.val(),
				email: inputEmail.val(),
				phone: inputPhone.val()};	
	
		e.preventDefault();
		$.ajax({
			url: '//formspree.io/{{ site.email }}',
			method: 'POST',
			data: messageData,
			dataType: 'json',
			beforeSend: function() {
				$contactForm.append('<div class="alert alert--loading">Sending message…</div>');
			},
			success: function(data) {
				$contactForm.find('.alert--loading').hide();
				$contactForm.append('<div class="alert alert--success">Message sent!</div>');
			},
			error: function(err) {
				$contactForm.find('.alert--loading').hide();
				$contactForm.append('<div class="alert alert--error">Ops, there was an error. ' + err.responseText + '</div>');
			}
		});
	});
});
</script>
<div class="row">
<div class="col-md-10">
<h3> Tiene preguntas?</h3>
<h5> Yo tengo respuestas (algunas)</h5> 
<p>Necesita contactarme? O solo saludar :)! No dude en dejarme su mensaje!</p>
        <form name="sendForm" id="sendForm" method="post">
            <div class="row">
                <div class="col-md-12">
                    <label>Nombre</label>
                    <input type="text" class="form-control" placeholder="Name" id="name" name="name" >
                </div>
            </div>
            <div class="row">
                <div class="col-md-12">
                    <label>Correo Electronico</label>
                    <input type="email" class="form-control" placeholder="Email Address" id="email" name="email">
                </div>
            </div>
            <div class="row">
                <div class="col-md-12">
                    <label>Numero Telefonico</label>
                    <input type="tel" class="form-control" placeholder="Phone Number" id="phone" name="phone">
                </div>
            </div>
            <div class="row">
                <div class="col-md-12">
                    <label>Mensaje</label>
                    <textarea rows="5" class="form-control" placeholder="Message" id="message" name="message"></textarea>
                </div>
            </div>
            <div class="row">
                <div class="col-md-12">
                    <button type="submit" class="btn-default">Enviar</button>
                </div>
            </div>
        </form>
</div>

</div>

