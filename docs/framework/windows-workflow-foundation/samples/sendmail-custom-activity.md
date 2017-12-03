---
title: Atividade personalizado de SendMail
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fb8454d3e1e679154bc016e37b83c3ac4ff6768
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="ff178-102">Atividade personalizado de SendMail</span><span class="sxs-lookup"><span data-stu-id="ff178-102">SendMail Custom Activity</span></span>
<span data-ttu-id="ff178-103">Este exemplo demonstra como criar uma atividade personalizada que derive de <xref:System.Activities.AsyncCodeActivity> para enviar email SMTP usando para uso em um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ff178-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="ff178-104">A atividade personalizado usa os recursos de <xref:System.Net.Mail.SmtpClient> de forma assíncrona enviar email e enviar email com autenticação.</span><span class="sxs-lookup"><span data-stu-id="ff178-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send e-mail asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="ff178-105">Também fornece alguns recursos de usuário final como o modo de teste, a substituição de token, os modelos de arquivo, e o caminho da operação de teste.</span><span class="sxs-lookup"><span data-stu-id="ff178-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="ff178-106">A tabela a seguir detalha os argumentos para atividades de `SendMail` .</span><span class="sxs-lookup"><span data-stu-id="ff178-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="ff178-107">Nome</span><span class="sxs-lookup"><span data-stu-id="ff178-107">Name</span></span>|<span data-ttu-id="ff178-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="ff178-108">Type</span></span>|<span data-ttu-id="ff178-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff178-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="ff178-110">Host</span><span class="sxs-lookup"><span data-stu-id="ff178-110">Host</span></span>|<span data-ttu-id="ff178-111">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ff178-111">String</span></span>|<span data-ttu-id="ff178-112">Endereço do host de servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="ff178-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="ff178-113">Porta</span><span class="sxs-lookup"><span data-stu-id="ff178-113">Port</span></span>|<span data-ttu-id="ff178-114">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ff178-114">String</span></span>|<span data-ttu-id="ff178-115">Porta de serviço SMTP no host.</span><span class="sxs-lookup"><span data-stu-id="ff178-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="ff178-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="ff178-116">EnableSsl</span></span>|<span data-ttu-id="ff178-117">bool</span><span class="sxs-lookup"><span data-stu-id="ff178-117">bool</span></span>|<span data-ttu-id="ff178-118">Especifica se <xref:System.Net.Mail.SmtpClient> usar secure sockets (SSL) para criptografar a conexão.</span><span class="sxs-lookup"><span data-stu-id="ff178-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="ff178-119">UserName</span><span class="sxs-lookup"><span data-stu-id="ff178-119">UserName</span></span>|<span data-ttu-id="ff178-120">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ff178-120">String</span></span>|<span data-ttu-id="ff178-121">Nome de usuário para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.</span><span class="sxs-lookup"><span data-stu-id="ff178-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="ff178-122">Senha</span><span class="sxs-lookup"><span data-stu-id="ff178-122">Password</span></span>|<span data-ttu-id="ff178-123">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ff178-123">String</span></span>|<span data-ttu-id="ff178-124">Senha para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.</span><span class="sxs-lookup"><span data-stu-id="ff178-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="ff178-125">Assunto</span><span class="sxs-lookup"><span data-stu-id="ff178-125">Subject</span></span>|<span data-ttu-id="ff178-126"><xref:System.Activities.InArgument%601>\<cadeia de caracteres ></span><span class="sxs-lookup"><span data-stu-id="ff178-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="ff178-127">Assunto de mensagem.</span><span class="sxs-lookup"><span data-stu-id="ff178-127">Subject of the message.</span></span>|  
|<span data-ttu-id="ff178-128">Corpo</span><span class="sxs-lookup"><span data-stu-id="ff178-128">Body</span></span>|<span data-ttu-id="ff178-129"><xref:System.Activities.InArgument%601>\<cadeia de caracteres ></span><span class="sxs-lookup"><span data-stu-id="ff178-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="ff178-130">Corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="ff178-130">Body of the message.</span></span>|  
|<span data-ttu-id="ff178-131">Anexos</span><span class="sxs-lookup"><span data-stu-id="ff178-131">Attachments</span></span>|<span data-ttu-id="ff178-132"><xref:System.Activities.InArgument%601>\<cadeia de caracteres ></span><span class="sxs-lookup"><span data-stu-id="ff178-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="ff178-133">Coleção de anexo usada para armazenar dados anexados a esta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="ff178-133">Attachment collection used to store data attached to this e-mail message.</span></span>|  
|<span data-ttu-id="ff178-134">De</span><span class="sxs-lookup"><span data-stu-id="ff178-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="ff178-135">O endereço para esta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="ff178-135">From address for this e-mail message.</span></span>|  
|<span data-ttu-id="ff178-136">Para</span><span class="sxs-lookup"><span data-stu-id="ff178-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="ff178-137">Trata da coleção que contém os destinatários esta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="ff178-137">Address collection that contains the recipients of this e-mail message.</span></span>|  
|<span data-ttu-id="ff178-138">CÓPIA CARBONO</span><span class="sxs-lookup"><span data-stu-id="ff178-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="ff178-139">Trata da coleção que contém os destinatários de (CC) de impressão carbono para esta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="ff178-139">Address collection that contains the carbon copy (CC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="ff178-140">BCC</span><span class="sxs-lookup"><span data-stu-id="ff178-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="ff178-141">Trata da coleção que contém os destinatários de (BCC) de impressão carbono cego para esta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="ff178-141">Address collection that contains the blind carbon copy (BCC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="ff178-142">Tokens</span><span class="sxs-lookup"><span data-stu-id="ff178-142">Tokens</span></span>|<span data-ttu-id="ff178-143"><xref:System.Activities.InArgument%601>< IDictionary\<cadeia de caracteres, cadeia de caracteres >></span><span class="sxs-lookup"><span data-stu-id="ff178-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="ff178-144">Tokens a substituição no corpo.</span><span class="sxs-lookup"><span data-stu-id="ff178-144">Tokens to replace in the body.</span></span> <span data-ttu-id="ff178-145">Esse recurso permite que os usuários especifiquem alguns valores no corpo do que pode ser substituído pelos tokens fornecidos posteriormente usando essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="ff178-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="ff178-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="ff178-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="ff178-147">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ff178-147">String</span></span>|<span data-ttu-id="ff178-148">Caminho de um modelo para o corpo.</span><span class="sxs-lookup"><span data-stu-id="ff178-148">Path of a template for the body.</span></span> <span data-ttu-id="ff178-149">A atividade de `SendMail` copia o conteúdo do arquivo a sua propriedade body.</span><span class="sxs-lookup"><span data-stu-id="ff178-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="ff178-150">O modelo pode conter os tokens que são substituídos pelos conteúdos da propriedade tokens.</span><span class="sxs-lookup"><span data-stu-id="ff178-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="ff178-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="ff178-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="ff178-152">Quando essa propriedade é definida, todos os email são enviados para o endereço especificado nele.</span><span class="sxs-lookup"><span data-stu-id="ff178-152">When this property is set, all e-mails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="ff178-153">Esta propriedade destina-se a ser usada ao testar fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="ff178-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="ff178-154">Por exemplo, quando você desejar se certificar de que todos os email são enviados sem enviar aos destinatários reais.</span><span class="sxs-lookup"><span data-stu-id="ff178-154">For example, when you want to make sure that all e-mails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="ff178-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="ff178-155">TestDropPath</span></span>|<span data-ttu-id="ff178-156">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="ff178-156">String</span></span>|<span data-ttu-id="ff178-157">Quando essa propriedade é definida, todos os email são salvos também no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="ff178-157">When this property is set, all e-mails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="ff178-158">Esta propriedade destina-se a ser usada quando você está testando ou depurando fluxos de trabalho, para certificar-se de que o formato e conteúdo de email de saída são apropriadas.</span><span class="sxs-lookup"><span data-stu-id="ff178-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing e-mails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="ff178-159">Conteúdo de solução</span><span class="sxs-lookup"><span data-stu-id="ff178-159">Solution Contents</span></span>  
 <span data-ttu-id="ff178-160">A solução contém dois projetos.</span><span class="sxs-lookup"><span data-stu-id="ff178-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="ff178-161">Projeto</span><span class="sxs-lookup"><span data-stu-id="ff178-161">Project</span></span>|<span data-ttu-id="ff178-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff178-162">Description</span></span>|<span data-ttu-id="ff178-163">Arquivos importantes</span><span class="sxs-lookup"><span data-stu-id="ff178-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="ff178-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="ff178-164">SendMail</span></span>|<span data-ttu-id="ff178-165">A atividade de SendMail</span><span class="sxs-lookup"><span data-stu-id="ff178-165">The SendMail activity</span></span>|<span data-ttu-id="ff178-166">1.  SendMail.cs: implementação para atividades principal</span><span class="sxs-lookup"><span data-stu-id="ff178-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="ff178-167">2.  SendMailDesigner.xaml e SendMailDesigner.xaml.cs: designer para atividades de SendMail</span><span class="sxs-lookup"><span data-stu-id="ff178-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="ff178-168">3.  MailTemplateBody.htm: modelo para o email é mandado.</span><span class="sxs-lookup"><span data-stu-id="ff178-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="ff178-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="ff178-169">SendMailTestClient</span></span>|<span data-ttu-id="ff178-170">Cliente para testar a atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="ff178-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="ff178-171">Este projeto mostra duas maneiras para chamar a atividade de SendMail: declarativamente, e programaticamente.</span><span class="sxs-lookup"><span data-stu-id="ff178-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="ff178-172">1.  Sequence1.xaml: fluxo de trabalho que chama a atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="ff178-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="ff178-173">2.  Module.vb: chama Sequence1 e também cria um fluxo de trabalho de programação que usa SendMail.</span><span class="sxs-lookup"><span data-stu-id="ff178-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="ff178-174">Configuração adicional de atividade de SendMail</span><span class="sxs-lookup"><span data-stu-id="ff178-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="ff178-175">Embora não mostrado no exemplo, os usuários podem executar a configuração de adição de atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="ff178-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="ff178-176">As três seções a seguir demonstram como este é feita.</span><span class="sxs-lookup"><span data-stu-id="ff178-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="ff178-177">Enviando um email usando os tokens especificados no corpo</span><span class="sxs-lookup"><span data-stu-id="ff178-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="ff178-178">Este trecho de código demonstra como você pode enviar email com tokens no corpo.</span><span class="sxs-lookup"><span data-stu-id="ff178-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="ff178-179">Observe como os tokens são fornecidos na propriedade body.</span><span class="sxs-lookup"><span data-stu-id="ff178-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="ff178-180">Os valores para estes tokens são fornecidos para a propriedade tokens.</span><span class="sxs-lookup"><span data-stu-id="ff178-180">Values for those tokens are provided to the tokens property.</span></span>  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="ff178-181">Enviando um email usando um modelo</span><span class="sxs-lookup"><span data-stu-id="ff178-181">Sending an email using a template</span></span>  
 <span data-ttu-id="ff178-182">Este trecho mostra como enviar um email usando tokens de um modelo no corpo.</span><span class="sxs-lookup"><span data-stu-id="ff178-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="ff178-183">Observe que ao definir a propriedade de `BodyTemplateFilePath` não precisamos de fornecer o valor para a propriedade body (o conteúdo do arquivo de modelo serão copiados para o corpo).</span><span class="sxs-lookup"><span data-stu-id="ff178-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="ff178-184">Enviar email no modo de teste</span><span class="sxs-lookup"><span data-stu-id="ff178-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="ff178-185">Este trecho de código mostra como definir as duas propriedades de teste: definindo `TestMailTo` para todas as mensagens serão enviadas para john.doe@contoso.con (sem levar em consideração dos valores de para, Cc, Cco).</span><span class="sxs-lookup"><span data-stu-id="ff178-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="ff178-186">Definindo TestDropPath todos os email de saída também serão gravados no caminho fornecido.</span><span class="sxs-lookup"><span data-stu-id="ff178-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="ff178-187">Essas propriedades podem ser definidas independentes (não são relacionadas).</span><span class="sxs-lookup"><span data-stu-id="ff178-187">These properties can be set independently (they are not related).</span></span>  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="ff178-188">Instruções de configuração</span><span class="sxs-lookup"><span data-stu-id="ff178-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="ff178-189">O acesso a um servidor SMTP é necessário para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="ff178-189">Access to a SMTP server is required for this sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="ff178-190">Configurando um servidor SMTP, consulte os links a seguir.</span><span class="sxs-lookup"><span data-stu-id="ff178-190"> setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="ff178-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="ff178-191">Microsoft Technet</span></span>](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="ff178-192">Configurando o serviço SMTP (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="ff178-192">Configuring the SMTP Service (IIS 6.0)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="ff178-193">IIS 7.0: Configurar o email SMTP</span><span class="sxs-lookup"><span data-stu-id="ff178-193">IIS 7.0: Configure SMTP E-Mail</span></span>](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="ff178-194">Como instalar o serviço SMTP</span><span class="sxs-lookup"><span data-stu-id="ff178-194">How to Install the SMTP Service</span></span>](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="ff178-195">Os emuladores SMTP fornecidos por terceiros estão disponíveis para download.</span><span class="sxs-lookup"><span data-stu-id="ff178-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="ff178-196">Para executar este exemplo</span><span class="sxs-lookup"><span data-stu-id="ff178-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="ff178-197">Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="ff178-197">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="ff178-198">Certifique-se de que você tem acesso a um servidor SMTP válido.</span><span class="sxs-lookup"><span data-stu-id="ff178-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="ff178-199">Consulte as instruções de configuração.</span><span class="sxs-lookup"><span data-stu-id="ff178-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="ff178-200">Configurar o programa com seu endereço do servidor, e e endereços de email.</span><span class="sxs-lookup"><span data-stu-id="ff178-200">Configure the program with your server address, and From and To e-mail addresses.</span></span>  
  
     <span data-ttu-id="ff178-201">Para executar corretamente esse exemplo, você pode precisar configurar o valor e endereços de email e o endereço de servidor SMTP em Module.vb e em Sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="ff178-201">To correctly run this sample, you may need to configure the value of From and To e-mail addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="ff178-202">Você precisará alterar o endereço nos dois lugares como o envia email de programa em duas maneiras diferentes</span><span class="sxs-lookup"><span data-stu-id="ff178-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="ff178-203">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="ff178-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="ff178-204">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="ff178-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ff178-205">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="ff178-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ff178-206">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="ff178-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ff178-207">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="ff178-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ff178-208">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="ff178-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`