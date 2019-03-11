# SendMailUsingSendGrid
Send Mail Using Send Grid



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
