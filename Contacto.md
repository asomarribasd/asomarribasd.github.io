---
layout: page
excerpt: "Contacta a Ahmed"
title: "Contacto"
permalink: /contacto/
---

<script>
$(document).ready(function(){
	var $contactForm = $("#sendForm");
	$contactForm.submit(function(e) {
	alert("Got it!");
		e.preventDefault();
		$.ajax({
			url: '//formspree.io/{{ site.email }}',
			type: 'post',
			data: "data=" + $($contactForm).serialize(),
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
				$contactForm.append('<div class="alert alert--error">Ops, there was an error.</div>');
			}
		});
	});
});
</script>
<div class="row">

    <div class="col-lg-10 col-lg-offset-1">
    <h3> Tiene preguntas? </h3>

<h4> Yo tengo respuestas (algunas) </h4> 

        <p>Necesita contactarme? Puede llenar el formulario y le contactare en menos de 24 horas!</p>
        <form name="sendForm" id="sendForm" method="post">
            <div class="row control-group">
                <div class="form-group col-xs-12 floating-label-form-group controls">
                    <label>Name</label>
                    <input type="text" class="form-control" placeholder="Name" id="name" required="" data-validation-required-message="Please enter your name." aria-invalid="false">
                    <p class="help-block text-danger"></p>
                </div>
            </div>
            <div class="row control-group">
                <div class="form-group col-xs-12 floating-label-form-group controls">
                    <label>Email Address</label>
                    <input type="email" class="form-control" placeholder="Email Address" id="email" required="" data-validation-required-message="Please enter your email address.">
                    <p class="help-block text-danger"></p>
                </div>
            </div>
            <div class="row control-group">
                <div class="form-group col-xs-12 floating-label-form-group controls">
                    <label>Phone Number</label>
                    <input type="tel" class="form-control" placeholder="Phone Number" id="phone" required="" data-validation-required-message="Please enter your phone number.">
                    <p class="help-block text-danger"></p>
                </div>
            </div>
            <div class="row control-group">
                <div class="form-group col-xs-12 floating-label-form-group controls">
                    <label>Message</label>
                    <textarea rows="5" class="form-control" placeholder="Message" id="message" required="" data-validation-required-message="Please enter a message."></textarea>
                    <p class="help-block text-danger"></p>
                </div>
            </div>
            <br>
            <div id="success"></div>
            <div class="row">
                <div class="form-group col-xs-12">
                    <button type="submit" class="btn btn-default">Send</button>
                </div>
            </div>
        </form>
    </div>

</div>

