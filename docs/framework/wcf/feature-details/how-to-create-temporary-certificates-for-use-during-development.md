---
title: Como criar certificados temporários para uso durante o desenvolvimento
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
ms.openlocfilehash: d3b051c7ea152606721388ea35b6f508eada1c5d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524359"
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Como criar certificados temporários para uso durante o desenvolvimento
Ao desenvolver um serviço seguro ou o cliente usando o Windows Communication Foundation (WCF), muitas vezes é necessário fornecer um certificado X.509 a ser usado como uma credencial. O certificado normalmente faz parte de uma cadeia de certificados com uma autoridade raiz encontrado no repositório de autoridades de certificação raiz confiáveis do computador. Ter uma cadeia de certificados permite que você definir o escopo de um conjunto de certificados onde normalmente na autoridade raiz é de sua organização ou a unidade de negócios. Para emular isso em tempo de desenvolvimento, você pode criar dois certificados para satisfazer os requisitos de segurança. A primeira é um certificado autoassinado que é colocado no repositório de autoridades de certificação raiz confiáveis, e o segundo certificado é criado a partir do primeiro e é colocado no repositório pessoal do Local do computador local ou o repositório pessoal das Local do usuário atual. Este tópico explica as etapas para criar esses dois certificados usando o [ferramenta de criação de certificado (MakeCert.exe)](https://go.microsoft.com/fwlink/?LinkId=248185), que é fornecido pelo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]
>  Os certificados que gera a ferramenta de criação de certificação são fornecidos somente para testes. Ao implantar um serviço ou cliente, certifique-se de usar um certificado apropriado fornecido por uma autoridade de certificação. Isso pode ser de um [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificado de servidor em sua organização ou por terceiros.  
>   
>  Por padrão, o [Makecert.exe (Certificate Creation Tool)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) cria certificados de autoridade cuja raiz é chamada "agência raiz **."** Como a agência"raiz" não está no repositório de autoridades de certificação raiz confiáveis, assim, esses certificados inseguro. Criando um certificado autoassinado que é colocado em autoridades de certificação raiz confiáveis store permite que você crie um ambiente de desenvolvimento que mais de perto simula o ambiente de implantação.  
  
 Para obter mais informações sobre como criar e usar certificados, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). Para obter mais informações sobre como usar um certificado como uma credencial, consulte [protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Para obter um tutorial sobre como usar a tecnologia Microsoft Authenticode, consulte [visões gerais de Authenticode e tutoriais](https://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Para criar um certificado de autoridade raiz autoassinado e exportar a chave privada  
  
1.  Use a ferramenta de MakeCert.exe com as seguintes opções:  
  
    1.  `-n` `subjectName`. Especifica o nome da entidade. A convenção é prefixar o nome da entidade com "CN =" de "Common Name".  
  
    2.  `-r`. Especifica que o certificado autoassinado.  
  
    3.  `-sv` `privateKeyFile`. Especifica o arquivo que contém o contêiner de chave privada.  
  
     Por exemplo, o comando a seguir cria um certificado autoassinado com o nome da entidade "CN = TempCA."  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Você será solicitado a fornecer uma senha para proteger a chave privada. Esta senha é necessária quando a criação de um certificado assinado por esse certificado raiz.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Para criar um novo certificado assinado por um certificado de autoridade raiz  
  
1.  Use a ferramenta de MakeCert.exe com as seguintes opções:  
  
    1.  `-sk` `subjectKey`. O local do contêiner de chave da entidade que contém a chave privada. Se um contêiner de chave não existir, ele é criado. Se nenhuma das opções de sk - ou - VA for usada, um contêiner de chave chamado JoeSoft é criado por padrão.  
  
    2.  `-n` `subjectName`. Especifica o nome da entidade. A convenção é prefixar o nome da entidade com "CN =" de "Common Name".  
  
    3.  `-iv` `issuerKeyFile`. Especifica o arquivo de chave privada do emissor.  
  
    4.  `-ic` `issuerCertFile`. Especifica o local do certificado do emissor.  
  
     Por exemplo, o comando a seguir cria um certificado assinado pela `TempCA` certificado de autoridade raiz com um nome de entidade `"CN=SignedByCA"` usando a chave privada do emissor.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalação de um certificado de Store de autoridades de certificação raiz confiável  
 Depois de criar um certificado autoassinado, você pode instalá-lo no repositório de autoridades de certificação raiz confiáveis. Todos os certificados são assinados com o certificado no momento são confiáveis para o computador. Por esse motivo, exclua o certificado do armazenamento assim que você não precisa mais dela. Quando você excluir este certificado de autoridade raiz, todos os outros certificados assinados com ela se tornou não autorizados. Certificados de autoridade raiz são simplesmente um mecanismo pelo qual um grupo de certificados pode ser definido conforme o necessário. Por exemplo, em aplicativos ponto a ponto, há geralmente sem a necessidade de uma autoridade raiz porque você simplesmente confia na identidade de um indivíduo por seu certificado fornecido.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Para instalar um certificado autoassinado em autoridades de certificação raiz confiáveis  
  
1.  Abra o snap-in de certificado. Para obter mais informações, confira [Como exibir certificados com o snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Abra a pasta para armazenar o certificado, ou o **computador Local** ou o **usuário atual**.  
  
3.  Abra o **autoridades de certificação raiz confiáveis** pasta.  
  
4.  Com o botão direito do **certificados** pasta e clique em **todas as tarefas**, em seguida, clique em **importação**.  
  
5.  Siga o assistente na tela instruções para importar o TempCa.cer no repositório.  
  
## <a name="using-certificates-with-wcf"></a>Usar certificados com o WCF  
 Depois que você configurar os certificados temporários, você pode usá-los para desenvolver soluções do WCF que especificam certificados como um tipo de credencial de cliente. Por exemplo, a configuração de XML a seguir especifica segurança de mensagem e um certificado como o tipo de credencial de cliente.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Para especificar um certificado como o tipo de credencial de cliente  
  
-   No arquivo de configuração para um serviço, use o seguinte XML para definir o modo de segurança para a mensagem e o tipo de credencial de cliente para o certificado.  
  
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
  
 No arquivo de configuração para um cliente, use o seguinte XML para especificar que o certificado for encontrado no repositório do usuário e pode ser encontrado pesquisando o campo SubjectName para o valor de "CohoWinery."  
  
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
  
 Para obter mais informações sobre como usar certificados no WCF, consulte [trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Certifique-se de excluir quaisquer certificados de autoridade raiz temporária dos **autoridades de certificação raiz confiáveis** e **pessoais** pastas clicando duas vezes no certificado e, em seguida, clicando em  **Excluir**.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Como exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
