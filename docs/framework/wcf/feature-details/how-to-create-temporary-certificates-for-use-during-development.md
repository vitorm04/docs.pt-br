---
title: 'Como: criar certificados temporários para uso durante o desenvolvimento'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d45f18b0b8fe4e0cc9667091e166c80691faa2d4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58921319"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="72d7d-102">Como: criar certificados temporários para uso durante o desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="72d7d-102">How to: Create Temporary Certificates for Use During Development</span></span>

<span data-ttu-id="72d7d-103">Ao desenvolver um serviço seguro ou o cliente usando o Windows Communication Foundation (WCF), muitas vezes é necessário fornecer um certificado X.509 a ser usado como uma credencial.</span><span class="sxs-lookup"><span data-stu-id="72d7d-103">When developing a secure service or client using Windows Communication Foundation (WCF), it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="72d7d-104">O certificado normalmente faz parte de uma cadeia de certificados com uma autoridade raiz encontrado no repositório de autoridades de certificação raiz confiáveis do computador.</span><span class="sxs-lookup"><span data-stu-id="72d7d-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="72d7d-105">Ter uma cadeia de certificados permite que você definir o escopo de um conjunto de certificados onde normalmente na autoridade raiz é de sua organização ou a unidade de negócios.</span><span class="sxs-lookup"><span data-stu-id="72d7d-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="72d7d-106">Para emular isso em tempo de desenvolvimento, você pode criar dois certificados para satisfazer os requisitos de segurança.</span><span class="sxs-lookup"><span data-stu-id="72d7d-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="72d7d-107">A primeira é um certificado autoassinado que é colocado no repositório de autoridades de certificação raiz confiáveis, e o segundo certificado é criado a partir do primeiro e é colocado no repositório pessoal do Local do computador local ou o repositório pessoal das Local do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="72d7d-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="72d7d-108">Este tópico explica as etapas para criar esses dois certificados usando o Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72d7d-108">This topic walks through the steps to create these two certificates using the Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72d7d-109">Os certificados que o cmdlet New-SelfSignedCertificate gera são fornecidos somente para testes.</span><span class="sxs-lookup"><span data-stu-id="72d7d-109">The certificates that the New-SelfSignedCertificate cmdlet generates are provided for testing purposes only.</span></span> <span data-ttu-id="72d7d-110">Ao implantar um serviço ou cliente, certifique-se de usar um certificado apropriado fornecido por uma autoridade de certificação.</span><span class="sxs-lookup"><span data-stu-id="72d7d-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="72d7d-111">Isso pode ser de um servidor de certificados do Windows Server em sua organização ou por terceiros.</span><span class="sxs-lookup"><span data-stu-id="72d7d-111">This could either be from a Windows Server certificate server in your organization or a third party.</span></span>
>
> <span data-ttu-id="72d7d-112">Por padrão, o [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet cria certificados autoassinados e esses certificados são inseguros.</span><span class="sxs-lookup"><span data-stu-id="72d7d-112">By default, the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet creates certificates that are self-signed and these certificates are insecure.</span></span> <span data-ttu-id="72d7d-113">Colocando os certificados autoassinados em autoridades de certificação raiz confiáveis store permite que você crie um ambiente de desenvolvimento que mais de perto simula o ambiente de implantação.</span><span class="sxs-lookup"><span data-stu-id="72d7d-113">Placing the self-signed certificates in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>

 <span data-ttu-id="72d7d-114">Para obter mais informações sobre como criar e usar certificados, consulte [trabalhando com certificados](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="72d7d-114">For more information about creating and using certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="72d7d-115">Para obter mais informações sobre como usar um certificado como uma credencial, consulte [protegendo serviços e clientes](securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="72d7d-115">For more information about using a certificate as a credential, see [Securing Services and Clients](securing-services-and-clients.md).</span></span> <span data-ttu-id="72d7d-116">Para obter um tutorial sobre como usar a tecnologia Microsoft Authenticode, consulte [visões gerais de Authenticode e tutoriais](https://go.microsoft.com/fwlink/?LinkId=88919).</span><span class="sxs-lookup"><span data-stu-id="72d7d-116">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](https://go.microsoft.com/fwlink/?LinkId=88919).</span></span>

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="72d7d-117">Para criar um certificado de autoridade raiz autoassinado e exportar a chave privada</span><span class="sxs-lookup"><span data-stu-id="72d7d-117">To create a self-signed root authority certificate and export the private key</span></span>

<span data-ttu-id="72d7d-118">O comando a seguir cria um certificado autoassinado com o nome da entidade "RootCA" no repositório pessoal do usuário atual.</span><span class="sxs-lookup"><span data-stu-id="72d7d-118">The following command creates a self-signed certificate with a subject name of "RootCA" in the Current User Personal store.</span></span>

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

<span data-ttu-id="72d7d-119">É necessário exportar o certificado para um arquivo PFX para que ele possa ser importado para onde são necessários em uma etapa posterior.</span><span class="sxs-lookup"><span data-stu-id="72d7d-119">We need to export the certificate to a PFX file so that it can be imported to where it's needed in a later step.</span></span> <span data-ttu-id="72d7d-120">Ao exportar um certificado com a chave privada, é necessária uma senha para protegê-lo.</span><span class="sxs-lookup"><span data-stu-id="72d7d-120">When exporting a certificate with the private key, a password is needed to protect it.</span></span> <span data-ttu-id="72d7d-121">Vamos salvar a senha em um `SecureString` e usar o [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet para exportar o certificado com a chave privada associada a um arquivo PFX.</span><span class="sxs-lookup"><span data-stu-id="72d7d-121">We save the password in a `SecureString` and use the [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet to export the certificate with the associated private key to a PFX file.</span></span> <span data-ttu-id="72d7d-122">Podemos também salvar apenas o certificado público em um arquivo de CRT usando o [certificado de exportação](/powershell/module/pkiclient/export-certificate) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="72d7d-122">We also save just the public certificate into a CRT file using the [Export-Certificate](/powershell/module/pkiclient/export-certificate) cmdlet.</span></span>

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="72d7d-123">Para criar um novo certificado assinado por um certificado de autoridade raiz</span><span class="sxs-lookup"><span data-stu-id="72d7d-123">To create a new certificate signed by a root authority certificate</span></span>

<span data-ttu-id="72d7d-124">O comando a seguir cria um certificado assinado pelo `RootCA` com um nome de assunto de "SignedByRootCA" usando a chave privada do emissor.</span><span class="sxs-lookup"><span data-stu-id="72d7d-124">The following command creates a certificate signed by the `RootCA` with a subject name of "SignedByRootCA" using the private key of the issuer.</span></span>

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

<span data-ttu-id="72d7d-125">Da mesma forma, salvamos o certificado assinado com a chave privada em um arquivo PFX e a chave pública em um arquivo de CRT.</span><span class="sxs-lookup"><span data-stu-id="72d7d-125">Similarly, we save the signed certificate with private key into a PFX file and just the public key into a CRT file.</span></span>

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="72d7d-126">Instalação de um certificado de Store de autoridades de certificação raiz confiável</span><span class="sxs-lookup"><span data-stu-id="72d7d-126">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>

<span data-ttu-id="72d7d-127">Depois de criar um certificado autoassinado, você pode instalá-lo no repositório de autoridades de certificação raiz confiáveis.</span><span class="sxs-lookup"><span data-stu-id="72d7d-127">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="72d7d-128">Todos os certificados são assinados com o certificado no momento são confiáveis para o computador.</span><span class="sxs-lookup"><span data-stu-id="72d7d-128">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="72d7d-129">Por esse motivo, exclua o certificado do armazenamento assim que você não precisa mais dela.</span><span class="sxs-lookup"><span data-stu-id="72d7d-129">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="72d7d-130">Quando você excluir este certificado de autoridade raiz, todos os outros certificados assinados com ela se tornou não autorizados.</span><span class="sxs-lookup"><span data-stu-id="72d7d-130">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="72d7d-131">Certificados de autoridade raiz são simplesmente um mecanismo pelo qual um grupo de certificados pode ser definido conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="72d7d-131">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="72d7d-132">Por exemplo, em aplicativos ponto a ponto, há geralmente sem a necessidade de uma autoridade raiz porque você simplesmente confia na identidade de um indivíduo por seu certificado fornecido.</span><span class="sxs-lookup"><span data-stu-id="72d7d-132">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="72d7d-133">Para instalar um certificado autoassinado em autoridades de certificação raiz confiáveis</span><span class="sxs-lookup"><span data-stu-id="72d7d-133">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>

1. <span data-ttu-id="72d7d-134">Abra o snap-in de certificado.</span><span class="sxs-lookup"><span data-stu-id="72d7d-134">Open the certificate snap-in.</span></span> <span data-ttu-id="72d7d-135">Para obter mais informações, confira [Como: Exibir certificados com o Snap-in do MMC](how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="72d7d-135">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

2. <span data-ttu-id="72d7d-136">Abra a pasta para armazenar o certificado, ou o **computador Local** ou o **usuário atual**.</span><span class="sxs-lookup"><span data-stu-id="72d7d-136">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>

3. <span data-ttu-id="72d7d-137">Abra o **autoridades de certificação raiz confiáveis** pasta.</span><span class="sxs-lookup"><span data-stu-id="72d7d-137">Open the **Trusted Root Certification Authorities** folder.</span></span>

4. <span data-ttu-id="72d7d-138">Com o botão direito do **certificados** pasta e clique em **todas as tarefas**, em seguida, clique em **importação**.</span><span class="sxs-lookup"><span data-stu-id="72d7d-138">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>

5. <span data-ttu-id="72d7d-139">Siga o assistente na tela instruções para importar o RootCA.pfx no repositório.</span><span class="sxs-lookup"><span data-stu-id="72d7d-139">Follow the on-screen wizard instructions to import the RootCA.pfx into the store.</span></span>

## <a name="using-certificates-with-wcf"></a><span data-ttu-id="72d7d-140">Usar certificados com o WCF</span><span class="sxs-lookup"><span data-stu-id="72d7d-140">Using certificates With WCF</span></span>

<span data-ttu-id="72d7d-141">Depois que você configurar os certificados temporários, você pode usá-los para desenvolver soluções do WCF que especificam certificados como um tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="72d7d-141">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="72d7d-142">Por exemplo, a configuração de XML a seguir especifica segurança de mensagem e um certificado como o tipo de credencial de cliente.</span><span class="sxs-lookup"><span data-stu-id="72d7d-142">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="72d7d-143">Para especificar um certificado como o tipo de credencial de cliente</span><span class="sxs-lookup"><span data-stu-id="72d7d-143">To specify a certificate as the client credential type</span></span>

1. <span data-ttu-id="72d7d-144">No arquivo de configuração para um serviço, use o seguinte XML para definir o modo de segurança para a mensagem e o tipo de credencial de cliente para o certificado.</span><span class="sxs-lookup"><span data-stu-id="72d7d-144">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>

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

2. <span data-ttu-id="72d7d-145">No arquivo de configuração para um cliente, use o seguinte XML para especificar que o certificado for encontrado no repositório do usuário e pode ser encontrado pesquisando o campo SubjectName para o valor de "CohoWinery."</span><span class="sxs-lookup"><span data-stu-id="72d7d-145">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>

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

<span data-ttu-id="72d7d-146">Para obter mais informações sobre como usar certificados no WCF, consulte [trabalhando com certificados](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="72d7d-146">For more information about using certificates in WCF, see [Working with Certificates](working-with-certificates.md).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="72d7d-147">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="72d7d-147">.NET Framework security</span></span>

<span data-ttu-id="72d7d-148">Certifique-se de excluir quaisquer certificados de autoridade raiz temporária dos **autoridades de certificação raiz confiáveis** e **pessoais** pastas clicando duas vezes no certificado e, em seguida, clicando em  **Excluir**.</span><span class="sxs-lookup"><span data-stu-id="72d7d-148">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>

## <a name="see-also"></a><span data-ttu-id="72d7d-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72d7d-149">See also</span></span>

- [<span data-ttu-id="72d7d-150">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="72d7d-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="72d7d-151">Como: Exibir certificados com o Snap-in do MMC</span><span class="sxs-lookup"><span data-stu-id="72d7d-151">How to: View Certificates with the MMC Snap-in</span></span>](how-to-view-certificates-with-the-mmc-snap-in.md)
- [<span data-ttu-id="72d7d-152">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="72d7d-152">Securing Services and Clients</span></span>](securing-services-and-clients.md)
