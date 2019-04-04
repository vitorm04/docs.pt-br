---
title: 'Como: criar certificados temporários para uso durante o desenvolvimento'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d45f18b0b8fe4e0cc9667091e166c80691faa2d4
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58921319"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Como: criar certificados temporários para uso durante o desenvolvimento

Ao desenvolver um serviço seguro ou o cliente usando o Windows Communication Foundation (WCF), muitas vezes é necessário fornecer um certificado X.509 a ser usado como uma credencial. O certificado normalmente faz parte de uma cadeia de certificados com uma autoridade raiz encontrado no repositório de autoridades de certificação raiz confiáveis do computador. Ter uma cadeia de certificados permite que você definir o escopo de um conjunto de certificados onde normalmente na autoridade raiz é de sua organização ou a unidade de negócios. Para emular isso em tempo de desenvolvimento, você pode criar dois certificados para satisfazer os requisitos de segurança. A primeira é um certificado autoassinado que é colocado no repositório de autoridades de certificação raiz confiáveis, e o segundo certificado é criado a partir do primeiro e é colocado no repositório pessoal do Local do computador local ou o repositório pessoal das Local do usuário atual. Este tópico explica as etapas para criar esses dois certificados usando o Powershell [New-SelfSignedCertificate)](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet.

> [!IMPORTANT]
> Os certificados que o cmdlet New-SelfSignedCertificate gera são fornecidos somente para testes. Ao implantar um serviço ou cliente, certifique-se de usar um certificado apropriado fornecido por uma autoridade de certificação. Isso pode ser de um servidor de certificados do Windows Server em sua organização ou por terceiros.
>
> Por padrão, o [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet cria certificados autoassinados e esses certificados são inseguros. Colocando os certificados autoassinados em autoridades de certificação raiz confiáveis store permite que você crie um ambiente de desenvolvimento que mais de perto simula o ambiente de implantação.

 Para obter mais informações sobre como criar e usar certificados, consulte [trabalhando com certificados](working-with-certificates.md). Para obter mais informações sobre como usar um certificado como uma credencial, consulte [protegendo serviços e clientes](securing-services-and-clients.md). Para obter um tutorial sobre como usar a tecnologia Microsoft Authenticode, consulte [visões gerais de Authenticode e tutoriais](https://go.microsoft.com/fwlink/?LinkId=88919).

## <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Para criar um certificado de autoridade raiz autoassinado e exportar a chave privada

O comando a seguir cria um certificado autoassinado com o nome da entidade "RootCA" no repositório pessoal do usuário atual.

```powershell
PS $rootCert = New-SelfSignedCertificate -CertStoreLocation cert:\CurrentUser\My -DnsName "RootCA" -TextExtension @("1.3.6.1.4.1.311.21.10={text}1.3.6.1.5.5.7.3.1,1.3.6.1.5.5.7.3.2")
```

É necessário exportar o certificado para um arquivo PFX para que ele possa ser importado para onde são necessários em uma etapa posterior. Ao exportar um certificado com a chave privada, é necessária uma senha para protegê-lo. Vamos salvar a senha em um `SecureString` e usar o [Export-PfxCertificate](/powershell/module/pkiclient/export-pfxcertificate) cmdlet para exportar o certificado com a chave privada associada a um arquivo PFX. Podemos também salvar apenas o certificado público em um arquivo de CRT usando o [certificado de exportação](/powershell/module/pkiclient/export-certificate) cmdlet.

```powershell
PS [System.Security.SecureString]$rootcertPassword = ConvertTo-SecureString -String "password" -Force -AsPlainText
PS [String]$rootCertPath = Join-Path -Path 'cert:\CurrentUser\My\' -ChildPath "$($rootcert.Thumbprint)"
PS Export-PfxCertificate -Cert $rootCertPath -FilePath 'RootCA.pfx' -Password $rootcertPassword
PS Export-Certificate -Cert $rootCertPath -FilePath 'RootCA.crt'
```

## <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Para criar um novo certificado assinado por um certificado de autoridade raiz

O comando a seguir cria um certificado assinado pelo `RootCA` com um nome de assunto de "SignedByRootCA" usando a chave privada do emissor.

```powershell
PS $testCert = New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "SignedByRootCA" -KeyExportPolicy Exportable -KeyLength 2048 -KeyUsage DigitalSignature,KeyEncipherment -Signer $rootCert
```

Da mesma forma, salvamos o certificado assinado com a chave privada em um arquivo PFX e a chave pública em um arquivo de CRT.

```powershell
PS [String]$testCertPath = Join-Path -Path 'cert:\LocalMachine\My\' -ChildPath "$($testCert.Thumbprint)"
PS Export-PfxCertificate -Cert $testCertPath -FilePath testcert.pfx -Password $rootcertPassword
PS Export-Certificate -Cert $testCertPath -FilePath testcert.crt
```

## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalação de um certificado de Store de autoridades de certificação raiz confiável

Depois de criar um certificado autoassinado, você pode instalá-lo no repositório de autoridades de certificação raiz confiáveis. Todos os certificados são assinados com o certificado no momento são confiáveis para o computador. Por esse motivo, exclua o certificado do armazenamento assim que você não precisa mais dela. Quando você excluir este certificado de autoridade raiz, todos os outros certificados assinados com ela se tornou não autorizados. Certificados de autoridade raiz são simplesmente um mecanismo pelo qual um grupo de certificados pode ser definido conforme o necessário. Por exemplo, em aplicativos ponto a ponto, há geralmente sem a necessidade de uma autoridade raiz porque você simplesmente confia na identidade de um indivíduo por seu certificado fornecido.

### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Para instalar um certificado autoassinado em autoridades de certificação raiz confiáveis

1. Abra o snap-in de certificado. Para obter mais informações, confira [Como: Exibir certificados com o Snap-in do MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

2. Abra a pasta para armazenar o certificado, ou o **computador Local** ou o **usuário atual**.

3. Abra o **autoridades de certificação raiz confiáveis** pasta.

4. Com o botão direito do **certificados** pasta e clique em **todas as tarefas**, em seguida, clique em **importação**.

5. Siga o assistente na tela instruções para importar o RootCA.pfx no repositório.

## <a name="using-certificates-with-wcf"></a>Usar certificados com o WCF

Depois que você configurar os certificados temporários, você pode usá-los para desenvolver soluções do WCF que especificam certificados como um tipo de credencial de cliente. Por exemplo, a configuração de XML a seguir especifica segurança de mensagem e um certificado como o tipo de credencial de cliente.

### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Para especificar um certificado como o tipo de credencial de cliente

1. No arquivo de configuração para um serviço, use o seguinte XML para definir o modo de segurança para a mensagem e o tipo de credencial de cliente para o certificado.

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

2. No arquivo de configuração para um cliente, use o seguinte XML para especificar que o certificado for encontrado no repositório do usuário e pode ser encontrado pesquisando o campo SubjectName para o valor de "CohoWinery."

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

Para obter mais informações sobre como usar certificados no WCF, consulte [trabalhando com certificados](working-with-certificates.md).

## <a name="net-framework-security"></a>Segurança do .NET Framework

Certifique-se de excluir quaisquer certificados de autoridade raiz temporária dos **autoridades de certificação raiz confiáveis** e **pessoais** pastas clicando duas vezes no certificado e, em seguida, clicando em  **Excluir**.

## <a name="see-also"></a>Consulte também

- [Trabalhando com certificados](working-with-certificates.md)
- [Como: exibir certificados com o snap-in do MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Protegendo serviços e clientes](securing-services-and-clients.md)
