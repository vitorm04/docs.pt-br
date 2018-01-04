---
title: "Como criar certificados temporários para uso durante o desenvolvimento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6c955c3498c830403f628b4805611fadc44d68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="d7998-102">Como criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="d7998-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="d7998-103">Ao desenvolver um serviço seguro ou o cliente usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], geralmente é necessário fornecer um certificado x. 509 a ser usado como uma credencial.</span><span class="sxs-lookup"><span data-stu-id="d7998-103">When developing a secure service or client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="d7998-104">Normalmente, o certificado é parte de uma cadeia de certificados com uma autoridade raiz encontrado no repositório de autoridades de certificação raiz confiáveis do computador.</span><span class="sxs-lookup"><span data-stu-id="d7998-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="d7998-105">Ter uma cadeia de certificados permite que você definir o escopo de um conjunto de certificados onde normalmente a autoridade raiz é de sua organização ou unidade de negócios.</span><span class="sxs-lookup"><span data-stu-id="d7998-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="d7998-106">Para emular isso em tempo de desenvolvimento, você pode criar dois certificados para satisfazer os requisitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="d7998-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="d7998-107">A primeira é um certificado autoassinado que é colocado no repositório de autoridades de certificação raiz confiáveis, e o segundo certificado é criado a partir do primeiro e é colocado no armazenamento pessoal do Local do computador local ou o repositório pessoal das Local do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="d7998-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="d7998-108">Este tópico descreve as etapas para criar esses dois certificados usando o [ferramenta de criação de certificado (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), que é fornecido pelo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span><span class="sxs-lookup"><span data-stu-id="d7998-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7998-109">Os certificados que a ferramenta de criação de certificação gera são fornecidos somente para testes.</span><span class="sxs-lookup"><span data-stu-id="d7998-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="d7998-110">Ao implantar um serviço ou cliente, certifique-se de usar um certificado apropriado fornecido por uma autoridade de certificação.</span><span class="sxs-lookup"><span data-stu-id="d7998-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="d7998-111">Isso pode ser de um [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificado de servidor em sua organização ou de terceiros.</span><span class="sxs-lookup"><span data-stu-id="d7998-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="d7998-112">Por padrão, o [Makecert.exe (ferramenta de criação de certificado)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) cria certificados de autoridade cuja raiz é chamada "agência raiz**."**</span><span class="sxs-lookup"><span data-stu-id="d7998-112">By default, the [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency**."**</span></span> <span data-ttu-id="d7998-113">Como a agência"raiz" não está no repositório de autoridades de certificação raiz confiáveis, isso faz com que esses certificados insegura.</span><span class="sxs-lookup"><span data-stu-id="d7998-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="d7998-114">Criando um certificado autoassinado que é colocado em autoridades de certificação raiz confiáveis repositório permite que você crie um ambiente de desenvolvimento que simula mais de perto de seu ambiente de implantação.</span><span class="sxs-lookup"><span data-stu-id="d7998-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d7998-115">criar e usar certificados, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="d7998-115"> creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d7998-116">usando um certificado como uma credencial, consulte [protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d7998-116"> using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="d7998-117">Para obter um tutorial sobre como usar a tecnologia Microsoft Authenticode, consulte [visões gerais de Authenticode e tutoriais](http://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="d7998-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](http://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="d7998-118">Para criar um certificado de autoridade raiz autoassinado e exportar a chave privada</span><span class="sxs-lookup"><span data-stu-id="d7998-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="d7998-119">Use a ferramenta MakeCert.exe com as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="d7998-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="d7998-120">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="d7998-120">`-n` `subjectName`.</span></span> <span data-ttu-id="d7998-121">Especifica o nome da entidade.</span><span class="sxs-lookup"><span data-stu-id="d7998-121">Specifies the subject name.</span></span> <span data-ttu-id="d7998-122">A convenção é prefixar o nome de entidade com "CN =" para "Nome comum".</span><span class="sxs-lookup"><span data-stu-id="d7998-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="d7998-123">`-r`.</span><span class="sxs-lookup"><span data-stu-id="d7998-123">`-r`.</span></span> <span data-ttu-id="d7998-124">Especifica que o certificado autoassinado.</span><span class="sxs-lookup"><span data-stu-id="d7998-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="d7998-125">`-sv` `privateKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="d7998-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="d7998-126">Especifica o arquivo que contém o contêiner de chave privado.</span><span class="sxs-lookup"><span data-stu-id="d7998-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="d7998-127">Por exemplo, o comando a seguir cria um certificado autoassinado com um nome de assunto de "CN = TempCA."</span><span class="sxs-lookup"><span data-stu-id="d7998-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="d7998-128">Você será solicitado a fornecer uma senha para proteger a chave privada.</span><span class="sxs-lookup"><span data-stu-id="d7998-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="d7998-129">Essa senha é necessária quando a criação de um certificado assinado por este certificado raiz.</span><span class="sxs-lookup"><span data-stu-id="d7998-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="d7998-130">Para criar um novo certificado assinado por um certificado de autoridade raiz</span><span class="sxs-lookup"><span data-stu-id="d7998-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="d7998-131">Use a ferramenta MakeCert.exe com as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="d7998-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="d7998-132">`-sk` `subjectKey`.</span><span class="sxs-lookup"><span data-stu-id="d7998-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="d7998-133">O local do contêiner de chave da entidade que contém a chave privada.</span><span class="sxs-lookup"><span data-stu-id="d7998-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="d7998-134">Se um contêiner de chave não existir, um será criado.</span><span class="sxs-lookup"><span data-stu-id="d7998-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="d7998-135">Se nenhuma das opções sk - ou - sv for usada, um contêiner de chave chamado JoeSoft é criado por padrão.</span><span class="sxs-lookup"><span data-stu-id="d7998-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="d7998-136">`-n` `subjectName`.</span><span class="sxs-lookup"><span data-stu-id="d7998-136">`-n` `subjectName`.</span></span> <span data-ttu-id="d7998-137">Especifica o nome da entidade.</span><span class="sxs-lookup"><span data-stu-id="d7998-137">Specifies the subject name.</span></span> <span data-ttu-id="d7998-138">A convenção é prefixar o nome de entidade com "CN =" para "Nome comum".</span><span class="sxs-lookup"><span data-stu-id="d7998-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="d7998-139">`-iv` `issuerKeyFile`.</span><span class="sxs-lookup"><span data-stu-id="d7998-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="d7998-140">Especifica o arquivo de chave privada do emissor.</span><span class="sxs-lookup"><span data-stu-id="d7998-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="d7998-141">`-ic` `issuerCertFile`.</span><span class="sxs-lookup"><span data-stu-id="d7998-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="d7998-142">Especifica o local do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="d7998-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="d7998-143">Por exemplo, o comando a seguir cria um certificado assinado pelo `TempCA` certificado de autoridade raiz com um nome de assunto de `"CN=SignedByCA"` usando a chave privada do emissor.</span><span class="sxs-lookup"><span data-stu-id="d7998-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="d7998-144">Instalar um certificado no repositório de autoridades de certificação raiz confiável</span><span class="sxs-lookup"><span data-stu-id="d7998-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="d7998-145">Depois de criar um certificado autoassinado, você pode instalá-lo no repositório de autoridades de certificação raiz confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d7998-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="d7998-146">Todos os certificados são assinados com o certificado agora são confiáveis pelo computador.</span><span class="sxs-lookup"><span data-stu-id="d7998-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="d7998-147">Por esse motivo, exclua o certificado do armazenamento assim que você não precisa mais dela.</span><span class="sxs-lookup"><span data-stu-id="d7998-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="d7998-148">Quando você excluir este certificado de autoridade raiz, todos os outros certificados assinados com ele se tornar não autorizados.</span><span class="sxs-lookup"><span data-stu-id="d7998-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="d7998-149">Certificados de autoridade raiz são simplesmente um mecanismo pelo qual um grupo de certificados pode ser definido conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="d7998-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="d7998-150">Por exemplo, em aplicativos de ponto a ponto, há normalmente não precisa de uma autoridade raiz porque você confia simplesmente a identidade de um indivíduo por seu certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="d7998-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="d7998-151">Para instalar um certificado autoassinado em autoridades de certificação raiz confiáveis</span><span class="sxs-lookup"><span data-stu-id="d7998-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="d7998-152">Abra o snap-in de certificado.</span><span class="sxs-lookup"><span data-stu-id="d7998-152">Open the certificate snap-in.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="d7998-153">[Como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="d7998-153"> [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="d7998-154">Abra a pasta para armazenar o certificado, ou o **computador Local** ou **usuário atual**.</span><span class="sxs-lookup"><span data-stu-id="d7998-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="d7998-155">Abra o **autoridades de certificação raiz confiáveis** pasta.</span><span class="sxs-lookup"><span data-stu-id="d7998-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="d7998-156">Com o botão direito do **certificados** pasta e clique em **todas as tarefas**, em seguida, clique em **importação**.</span><span class="sxs-lookup"><span data-stu-id="d7998-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="d7998-157">Siga o assistente na tela instruções para importar o TempCa.cer para o armazenamento.</span><span class="sxs-lookup"><span data-stu-id="d7998-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="d7998-158">Usar certificados com o WCF</span><span class="sxs-lookup"><span data-stu-id="d7998-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="d7998-159">Depois que você configurar os certificados temporários, você pode usá-los para desenvolver soluções WCF que especifique certificados como um tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="d7998-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="d7998-160">Por exemplo, a configuração de XML a seguir especifica segurança de mensagem e um certificado como o tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="d7998-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="d7998-161">Para especificar um certificado como o tipo de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="d7998-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="d7998-162">No arquivo de configuração para um serviço, use o seguinte XML para definir o modo de segurança para a mensagem e o tipo de credencial de cliente para o certificado.</span><span class="sxs-lookup"><span data-stu-id="d7998-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 <span data-ttu-id="d7998-163">No arquivo de configuração para um cliente, use o seguinte XML para especificar que o certificado for encontrado no armazenamento do usuário e pode ser encontrado pesquisando o campo SubjectName para o valor "CohoWinery".</span><span class="sxs-lookup"><span data-stu-id="d7998-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="d7998-164">Para obter mais informações sobre como usar certificados no WCF, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="d7998-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d7998-165">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d7998-165">.NET Framework Security</span></span>  
 <span data-ttu-id="d7998-166">Certifique-se de excluir qualquer certificados de autoridade raiz temporário do **autoridades de certificação raiz confiáveis** e **pessoal** pastas clicando duas vezes no certificado, em seguida, clicando em  **Excluir**.</span><span class="sxs-lookup"><span data-stu-id="d7998-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7998-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7998-167">See Also</span></span>  
 [<span data-ttu-id="d7998-168">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="d7998-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d7998-169">Como exibir certificados com o Snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="d7998-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="d7998-170">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="d7998-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
