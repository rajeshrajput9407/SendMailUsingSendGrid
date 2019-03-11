# SendMailUsingSendGrid
Send Mail Using Send Grid


////////////////////////***************Send Mail Using Send Grid *****************//////////////////////////////

                var client = new SendGridClient("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");
                var msg = new SendGridMessage()
                {
                    From = new EmailAddress("duckscraper@hotmail.com", "Duck@123"),
                    Subject = "License Server",
                    //PlainTextContent = message,
                    HtmlContent = emailTemplate.ToString().Trim()
                };
                msg.AddTo(new EmailAddress(sendMailViewModel.ToMail));
                msg.SetClickTracking(false, false);
                var result = client.SendEmailAsync(msg);
                
                //////////********** USing SmTP Server ***********////////////////
                
            var emailTemplate = EmailTemplate.sendMessageFunction(sendMailViewModel);
            MailMessage objeto_mail = new MailMessage();
            SmtpClient client = new SmtpClient();
            client.Port = 587;
            client.Host = "smtp.gmail.com";
            client.Timeout = 10000;
            client.DeliveryMethod = SmtpDeliveryMethod.Network;
            client.UseDefaultCredentials = false;
            client.Credentials = new System.Net.NetworkCredential("rajesh.techprocomp@gmail.com", "Rajesh@123");
            client.EnableSsl = true;
            objeto_mail.From = new MailAddress("rajesh.techprocomp@gmail.com");
            objeto_mail.To.Add(new MailAddress(sendMailViewModel.ToMail));
            objeto_mail.Subject = "License Credentials";
            objeto_mail.IsBodyHtml = true;
            objeto_mail.Body = emailTemplate.ToString().Trim();
            client.Send(objeto_mail);
