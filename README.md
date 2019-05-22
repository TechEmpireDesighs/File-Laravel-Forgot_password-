# File-Laravel-Forgot_password-
This code will help individuals with a challage getting it righ on way out on Laravel Forgot password module Code Example


        <script src="<?php echo base_url("assets/js/jquery-1.9.1.js"); ?>"></script>
        <script type="text/javascript">
            $(document).ready(function() {
                $('#forgot_password').submit(function() {
                    $('#submit1').attr('disabled', 'true');
                    $('#submit2').attr('disabled', 'true');
                    var form = $(this);
                    $('#error').hide();
                    $('#success').hide();
                    $('#successMessage').html('');
                    var faction = "<?php echo site_url('signin/send_reset_password_link'); ?>";
                    var fdata = form.serialize();
                    $('#wrappermiddle').css("height", 192);
                    $.post(faction, fdata, function(rdata) {

                        var json = jQuery.parseJSON(rdata);

                        if (json.isSuccessful) {
                            $('#submit1').removeAttr('disabled');
                            $('#submit2').removeAttr('disabled');
                            $('#wrappermiddle').css("height", 300);
                            $('#successMessage').html(json.message + "<b>" + json.email + "</b>");
                            $('#success').show();
                        } else {
                            $('#submit1').removeAttr('disabled');
                            $('#submit2').removeAttr('disabled');
                            $('#errorMessage').html(json.message);
                            if (json.message.length == 36) {
                                $('#wrappermiddle').css("height", 265);
                                $('#error').css("padding-left", 85);
                                $('#error').css("padding-right", 62);
                            } else if (json.message.length == 38) {
                                $('#wrappermiddle').css("height", 276);
                                $('#error').css("padding-left", 64);
                                $('#error').css("padding-right", 62);
                            }
//                            
                            $('#error').show();
                            form.children('input[name="email"]').select();
                        }
                    });
                    return false;
                    $('#submit1').removeAttr('disabled');
                    $('#submit2').removeAttr('disabled');
                });
            });
        </script>
        <script src="<?php echo base_url("assets/js/jquery.validate.js"); ?>"></script>
