#Enviar una Solicitud
<br>

<meta name="description" content="Formulario de Contacto Dinex">
<script type="text/javascript"
        src="../solicitud.js"></script>        

<script src="https://code.jquery.com/jquery-1.10.2.js"></script>

<div id='result'>
<form id="contact_form" action="https://dinex.zendesk.com/requests/embedded/create/"; method="POST" onsubmit="return validateForm();" enctype="multipart/form-data" novalidate="novalidate">
  <div class="rowsubmit">
    <div class="col-sm-10">
        <label class="required" for="name">Nombre:</label>
        <input id="name" name="name" type="text" class="form-control" value="" size="30" />
        <span id="name_validation" class="error"></span>
    </div> 
  </div><br>
  
  <div class="rowsubmit">
    <div class="col-sm-10">
        <label class="required" for="email">Correo electrónico:</label>
        <input id="email" name="email" type="text" class="form-control" value="" size="30" />
        <span id="email_validation" class="error"></span>
    </div>
  </div><br>
 
   <div class="rowsubmit">
    <div class="col-sm-10">
        <label class="required" for="subject">Asunto:</label>
        <input id="subject" name="subject" type="text" class="form-control" value="" size="30" />
        <span id="subject_validation" class="error"></span>
    </div>
  </div><br>
  
  <div class="rowsubmit">
    <div class="col-sm-10">
        <label class="required" for="description">Mensaje:</label>
        <textarea id="description" name="description" class="form-control" rows="7" cols="30"></textarea>
        <span id="description_validation" class="error"></span>
    </div>
  </div><br>
  
  <div class="rowend">
    <div class="col-sm-10">
      <br>
      <button id='submit' type='submit' class='btn btn-primary'>Enviar</button>
    </div>
  </div>
  
</form>
</div>
<!-- JQuery to handle zendesk response -->
<script>
// Attach a submit handler to the form
$( "#contact_form" ).submit(function( event ) {
 
  // Stop form from submitting normally
  event.preventDefault();
 
  // Get some values from elements on the page:
  var $form = $( this ),
    data = $( "#contact_form" ).serialize(),
    url = $form.attr( "action" );
 
  // Send the data using post
  var posting = $.post( url, data );
 
  // Put the results in a div
  posting.done(function( data ) {
    var content = data.message.toString().split(' ');
    var response = "<b> Solicitud " + content[1] +  " fue creada exitosamente. </b> <br> <a href='/'>Volver</a>";
    $( "#result" ).empty().append( response );
    
  });
});
</script>
<!-- End JQuery -->

<!-- Disqus - Disable for now
# Deja tus comentarios 
<div id="disqus_thread"></div>
<script type="text/javascript">
    /* * * CONFIGURATION VARIABLES * * */
    var disqus_shortname = 'dinexinfo';

    /* * * DON'T EDIT BELOW THIS LINE * * */
    (function() {
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>      
End Disqus -->

