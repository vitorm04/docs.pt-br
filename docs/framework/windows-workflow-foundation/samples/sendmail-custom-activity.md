---
title: Atividade personalizado de SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 4dca15bfd3798b9282960663bea827f9323a1266
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547721"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="38c17-102">Atividade personalizado de SendMail</span><span class="sxs-lookup"><span data-stu-id="38c17-102">SendMail Custom Activity</span></span>
<span data-ttu-id="38c17-103">Este exemplo demonstra como criar uma atividade personalizada que derive de <xref:System.Activities.AsyncCodeActivity> para enviar email SMTP usando para uso em um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="38c17-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="38c17-104">A atividade personalizada usa os recursos do <xref:System.Net.Mail.SmtpClient> para enviar email de forma assíncrona e enviar emails com autenticação.</span><span class="sxs-lookup"><span data-stu-id="38c17-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="38c17-105">Também fornece alguns recursos de usuário final como o modo de teste, a substituição de token, os modelos de arquivo, e o caminho da operação de teste.</span><span class="sxs-lookup"><span data-stu-id="38c17-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="38c17-106">A tabela a seguir detalha os argumentos para atividades de `SendMail` .</span><span class="sxs-lookup"><span data-stu-id="38c17-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="38c17-107">Nome</span><span class="sxs-lookup"><span data-stu-id="38c17-107">Name</span></span>|<span data-ttu-id="38c17-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="38c17-108">Type</span></span>|<span data-ttu-id="38c17-109">Description</span><span class="sxs-lookup"><span data-stu-id="38c17-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="38c17-110">Host</span><span class="sxs-lookup"><span data-stu-id="38c17-110">Host</span></span>|<span data-ttu-id="38c17-111">String</span><span class="sxs-lookup"><span data-stu-id="38c17-111">String</span></span>|<span data-ttu-id="38c17-112">Endereço do host de servidor SMTP.</span><span class="sxs-lookup"><span data-stu-id="38c17-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="38c17-113">Porta</span><span class="sxs-lookup"><span data-stu-id="38c17-113">Port</span></span>|<span data-ttu-id="38c17-114">String</span><span class="sxs-lookup"><span data-stu-id="38c17-114">String</span></span>|<span data-ttu-id="38c17-115">Porta de serviço SMTP no host.</span><span class="sxs-lookup"><span data-stu-id="38c17-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="38c17-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="38c17-116">EnableSsl</span></span>|<span data-ttu-id="38c17-117">bool</span><span class="sxs-lookup"><span data-stu-id="38c17-117">bool</span></span>|<span data-ttu-id="38c17-118">Especifica se <xref:System.Net.Mail.SmtpClient> usar secure sockets (SSL) para criptografar a conexão.</span><span class="sxs-lookup"><span data-stu-id="38c17-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="38c17-119">UserName</span><span class="sxs-lookup"><span data-stu-id="38c17-119">UserName</span></span>|<span data-ttu-id="38c17-120">String</span><span class="sxs-lookup"><span data-stu-id="38c17-120">String</span></span>|<span data-ttu-id="38c17-121">Nome de usuário para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.</span><span class="sxs-lookup"><span data-stu-id="38c17-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="38c17-122">Senha</span><span class="sxs-lookup"><span data-stu-id="38c17-122">Password</span></span>|<span data-ttu-id="38c17-123">String</span><span class="sxs-lookup"><span data-stu-id="38c17-123">String</span></span>|<span data-ttu-id="38c17-124">Senha para configurar as credenciais para autenticar a propriedade de <xref:System.Net.Mail.SmtpClient.Credentials%2A> de retorno.</span><span class="sxs-lookup"><span data-stu-id="38c17-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="38c17-125">Assunto</span><span class="sxs-lookup"><span data-stu-id="38c17-125">Subject</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="38c17-126">Assunto de mensagem.</span><span class="sxs-lookup"><span data-stu-id="38c17-126">Subject of the message.</span></span>|  
|<span data-ttu-id="38c17-127">Corpo</span><span class="sxs-lookup"><span data-stu-id="38c17-127">Body</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="38c17-128">Corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="38c17-128">Body of the message.</span></span>|  
|<span data-ttu-id="38c17-129">Anexos</span><span class="sxs-lookup"><span data-stu-id="38c17-129">Attachments</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="38c17-130">Coleção de anexos usada para armazenar dados anexados a esta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="38c17-130">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="38c17-131">De</span><span class="sxs-lookup"><span data-stu-id="38c17-131">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="38c17-132">Endereço do remetente desta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="38c17-132">From address for this email message.</span></span>|  
|<span data-ttu-id="38c17-133">Para</span><span class="sxs-lookup"><span data-stu-id="38c17-133">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="38c17-134">Coleção de endereços que contém os destinatários desta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="38c17-134">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="38c17-135">CC</span><span class="sxs-lookup"><span data-stu-id="38c17-135">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="38c17-136">Coleção de endereços que contém destinatários de cópia carbono (CC) para esta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="38c17-136">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="38c17-137">BCC</span><span class="sxs-lookup"><span data-stu-id="38c17-137">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="38c17-138">Coleção de endereços que contém os destinatários da cópia oculta (Cco) desta mensagem de email.</span><span class="sxs-lookup"><span data-stu-id="38c17-138">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="38c17-139">Tokens</span><span class="sxs-lookup"><span data-stu-id="38c17-139">Tokens</span></span>|<span data-ttu-id="38c17-140"><xref:System.Activities.InArgument%601> IDictionary<\<string, string>></span><span class="sxs-lookup"><span data-stu-id="38c17-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="38c17-141">Tokens a substituição no corpo.</span><span class="sxs-lookup"><span data-stu-id="38c17-141">Tokens to replace in the body.</span></span> <span data-ttu-id="38c17-142">Esse recurso permite que os usuários especifiquem alguns valores no corpo do que pode ser substituído pelos tokens fornecidos posteriormente usando essa propriedade.</span><span class="sxs-lookup"><span data-stu-id="38c17-142">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="38c17-143">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="38c17-143">BodyTemplateFilePath</span></span>|<span data-ttu-id="38c17-144">String</span><span class="sxs-lookup"><span data-stu-id="38c17-144">String</span></span>|<span data-ttu-id="38c17-145">Caminho de um modelo para o corpo.</span><span class="sxs-lookup"><span data-stu-id="38c17-145">Path of a template for the body.</span></span> <span data-ttu-id="38c17-146">A atividade de `SendMail` copia o conteúdo do arquivo a sua propriedade body.</span><span class="sxs-lookup"><span data-stu-id="38c17-146">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="38c17-147">O modelo pode conter os tokens que são substituídos pelos conteúdos da propriedade tokens.</span><span class="sxs-lookup"><span data-stu-id="38c17-147">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="38c17-148">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="38c17-148">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="38c17-149">Quando essa propriedade é definida, todos os emails são enviados para o endereço especificado nele.</span><span class="sxs-lookup"><span data-stu-id="38c17-149">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="38c17-150">Esta propriedade destina-se a ser usada ao testar fluxos de trabalho.</span><span class="sxs-lookup"><span data-stu-id="38c17-150">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="38c17-151">Por exemplo, quando você deseja certificar-se de que todos os emails são enviados sem enviá-los aos destinatários reais.</span><span class="sxs-lookup"><span data-stu-id="38c17-151">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="38c17-152">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="38c17-152">TestDropPath</span></span>|<span data-ttu-id="38c17-153">String</span><span class="sxs-lookup"><span data-stu-id="38c17-153">String</span></span>|<span data-ttu-id="38c17-154">Quando essa propriedade é definida, todos os emails também são salvos no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="38c17-154">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="38c17-155">Essa propriedade deve ser usada quando você estiver testando ou Depurando fluxos de trabalho, para garantir que o formato e o conteúdo dos emails de saída sejam apropriados.</span><span class="sxs-lookup"><span data-stu-id="38c17-155">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="38c17-156">Conteúdo de solução</span><span class="sxs-lookup"><span data-stu-id="38c17-156">Solution Contents</span></span>  
 <span data-ttu-id="38c17-157">A solução contém dois projetos.</span><span class="sxs-lookup"><span data-stu-id="38c17-157">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="38c17-158">Projeto</span><span class="sxs-lookup"><span data-stu-id="38c17-158">Project</span></span>|<span data-ttu-id="38c17-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="38c17-159">Description</span></span>|<span data-ttu-id="38c17-160">Arquivos importantes</span><span class="sxs-lookup"><span data-stu-id="38c17-160">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="38c17-161">SendMail</span><span class="sxs-lookup"><span data-stu-id="38c17-161">SendMail</span></span>|<span data-ttu-id="38c17-162">A atividade de SendMail</span><span class="sxs-lookup"><span data-stu-id="38c17-162">The SendMail activity</span></span>|<span data-ttu-id="38c17-163">1. SendMail.cs: implementação para a atividade principal</span><span class="sxs-lookup"><span data-stu-id="38c17-163">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="38c17-164">2. SendMailDesigner. XAML e SendMailDesigner.xaml.cs: designer para a atividade SendMail</span><span class="sxs-lookup"><span data-stu-id="38c17-164">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="38c17-165">3. MailTemplateBody.htm: modelo para o email a ser enviado.</span><span class="sxs-lookup"><span data-stu-id="38c17-165">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="38c17-166">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="38c17-166">SendMailTestClient</span></span>|<span data-ttu-id="38c17-167">Cliente para testar a atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="38c17-167">Client to test the SendMail activity.</span></span>  <span data-ttu-id="38c17-168">Este projeto mostra duas maneiras para chamar a atividade de SendMail: declarativamente, e programaticamente.</span><span class="sxs-lookup"><span data-stu-id="38c17-168">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="38c17-169">1. Sequence1. XAML: fluxo de trabalho que invoca a atividade SendMail.</span><span class="sxs-lookup"><span data-stu-id="38c17-169">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="38c17-170">2. Program.cs: invoca Sequence1 e também cria um fluxo de trabalho programaticamente que usa o SendMail.</span><span class="sxs-lookup"><span data-stu-id="38c17-170">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="38c17-171">Configuração adicional de atividade de SendMail</span><span class="sxs-lookup"><span data-stu-id="38c17-171">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="38c17-172">Embora não mostrado no exemplo, os usuários podem executar a configuração de adição de atividade de SendMail.</span><span class="sxs-lookup"><span data-stu-id="38c17-172">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="38c17-173">As três seções a seguir demonstram como este é feita.</span><span class="sxs-lookup"><span data-stu-id="38c17-173">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="38c17-174">Enviando um email usando os tokens especificados no corpo</span><span class="sxs-lookup"><span data-stu-id="38c17-174">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="38c17-175">Este snippet de código demonstra como você pode enviar email com tokens no corpo.</span><span class="sxs-lookup"><span data-stu-id="38c17-175">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="38c17-176">Observe como os tokens são fornecidos na propriedade body.</span><span class="sxs-lookup"><span data-stu-id="38c17-176">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="38c17-177">Os valores para estes tokens são fornecidos para a propriedade tokens.</span><span class="sxs-lookup"><span data-stu-id="38c17-177">Values for those tokens are provided to the tokens property.</span></span>  
  
```csharp  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="38c17-178">Enviando um email usando um modelo</span><span class="sxs-lookup"><span data-stu-id="38c17-178">Sending an email using a template</span></span>  
 <span data-ttu-id="38c17-179">Este snippet mostra como enviar um email usando tokens de um modelo no corpo.</span><span class="sxs-lookup"><span data-stu-id="38c17-179">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="38c17-180">Observe que ao definir a propriedade de `BodyTemplateFilePath` não precisamos de fornecer o valor para a propriedade body (o conteúdo do arquivo de modelo serão copiados para o corpo).</span><span class="sxs-lookup"><span data-stu-id="38c17-180">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```csharp  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="38c17-181">Enviar email no modo de teste</span><span class="sxs-lookup"><span data-stu-id="38c17-181">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="38c17-182">Este trecho de código mostra como definir as duas propriedades de teste: ao definir `TestMailTo` como todas as mensagens serão enviadas `john.doe@contoso.con` (sem considerar os valores de para, CC, Cco).</span><span class="sxs-lookup"><span data-stu-id="38c17-182">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="38c17-183">Definindo TestDropPath todos os email de saída também serão gravados no caminho fornecido.</span><span class="sxs-lookup"><span data-stu-id="38c17-183">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="38c17-184">Essas propriedades podem ser definidas independentes (não são relacionadas).</span><span class="sxs-lookup"><span data-stu-id="38c17-184">These properties can be set independently (they are not related).</span></span>  
  
```csharp  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="38c17-185">Instruções de configuração</span><span class="sxs-lookup"><span data-stu-id="38c17-185">Set-Up Instructions</span></span>  
 <span data-ttu-id="38c17-186">O acesso a um servidor SMTP é necessário para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="38c17-186">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="38c17-187">Para obter mais informações sobre como configurar um servidor SMTP, consulte os links a seguir.</span><span class="sxs-lookup"><span data-stu-id="38c17-187">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="38c17-188">[Configurando o serviço SMTP (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="38c17-188">[Configuring the SMTP Service (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="38c17-189">[IIS 7.0: Configurar o email SMTP](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="38c17-189">[IIS 7.0: Configure SMTP E-Mail](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="38c17-190">[Como instalar o serviço SMTP](/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="38c17-190">[How to Install the SMTP Service](/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="38c17-191">Os emuladores SMTP fornecidos por terceiros estão disponíveis para download.</span><span class="sxs-lookup"><span data-stu-id="38c17-191">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="38c17-192">Para executar este exemplo</span><span class="sxs-lookup"><span data-stu-id="38c17-192">To run this sample</span></span>  
  
1. <span data-ttu-id="38c17-193">Usando o Visual Studio 2010, abra o arquivo de solução SendMail. sln.</span><span class="sxs-lookup"><span data-stu-id="38c17-193">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="38c17-194">Certifique-se de que você tem acesso a um servidor SMTP válido.</span><span class="sxs-lookup"><span data-stu-id="38c17-194">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="38c17-195">Consulte as instruções de configuração.</span><span class="sxs-lookup"><span data-stu-id="38c17-195">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="38c17-196">Configure o programa com seu endereço de servidor e de e para endereços de email.</span><span class="sxs-lookup"><span data-stu-id="38c17-196">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="38c17-197">Para executar corretamente este exemplo, talvez seja necessário configurar o valor de e para endereços de email e o endereço do servidor SMTP em Program.cs e em Sequence. XAML.</span><span class="sxs-lookup"><span data-stu-id="38c17-197">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="38c17-198">Você precisará alterar o endereço nos dois lugares como o envia email de programa em duas maneiras diferentes</span><span class="sxs-lookup"><span data-stu-id="38c17-198">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="38c17-199">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="38c17-199">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="38c17-200">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="38c17-200">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38c17-201">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="38c17-201">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38c17-202">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="38c17-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="38c17-203">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="38c17-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38c17-204">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="38c17-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
