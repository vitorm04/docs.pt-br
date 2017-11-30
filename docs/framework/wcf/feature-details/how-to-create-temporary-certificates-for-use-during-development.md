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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a1b386906c1d493a23d8a58f3540758d3ae0d26e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Como criar certificados temporários para uso durante o desenvolvimento
Ao desenvolver um serviço seguro ou o cliente usando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], geralmente é necessário fornecer um certificado x. 509 a ser usado como uma credencial. Normalmente, o certificado é parte de uma cadeia de certificados com uma autoridade raiz encontrado no repositório de autoridades de certificação raiz confiáveis do computador. Ter uma cadeia de certificados permite que você definir o escopo de um conjunto de certificados onde normalmente a autoridade raiz é de sua organização ou unidade de negócios. Para emular isso em tempo de desenvolvimento, você pode criar dois certificados para satisfazer os requisitos de segurança. A primeira é um certificado autoassinado que é colocado no repositório de autoridades de certificação raiz confiáveis, e o segundo certificado é criado a partir do primeiro e é colocado no armazenamento pessoal do Local do computador local ou o repositório pessoal das Local do usuário atual. Este tópico descreve as etapas para criar esses dois certificados usando o [ferramenta de criação de certificado (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), que é fornecido pelo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.  
  
> [!IMPORTANT]
>  Os certificados que a ferramenta de criação de certificação gera são fornecidos somente para testes. Ao implantar um serviço ou cliente, certifique-se de usar um certificado apropriado fornecido por uma autoridade de certificação. Isso pode ser de um [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificado de servidor em sua organização ou de terceiros.  
>   
>  Por padrão, o [Makecert.exe (ferramenta de criação de certificado)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) cria certificados de autoridade cuja raiz é chamada "agência raiz**."** Como a agência"raiz" não está no repositório de autoridades de certificação raiz confiáveis, isso faz com que esses certificados insegura. Criando um certificado autoassinado que é colocado em autoridades de certificação raiz confiáveis repositório permite que você crie um ambiente de desenvolvimento que simula mais de perto de seu ambiente de implantação.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]criar e usar certificados, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando um certificado como uma credencial, consulte [protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Para obter um tutorial sobre como usar a tecnologia Microsoft Authenticode, consulte [visões gerais de Authenticode e tutoriais](http://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Para criar um certificado de autoridade raiz autoassinado e exportar a chave privada  
  
1.  Use a ferramenta MakeCert.exe com as seguintes opções:  
  
    1.  `-n` `subjectName`. Especifica o nome da entidade. A convenção é prefixar o nome de entidade com "CN =" para "Nome comum".  
  
    2.  `-r`. Especifica que o certificado autoassinado.  
  
    3.  `-sv` `privateKeyFile`. Especifica o arquivo que contém o contêiner de chave privado.  
  
     Por exemplo, o comando a seguir cria um certificado autoassinado com um nome de assunto de "CN = TempCA."  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Você será solicitado a fornecer uma senha para proteger a chave privada. Essa senha é necessária quando a criação de um certificado assinado por este certificado raiz.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Para criar um novo certificado assinado por um certificado de autoridade raiz  
  
1.  Use a ferramenta MakeCert.exe com as seguintes opções:  
  
    1.  `-sk` `subjectKey`. O local do contêiner de chave da entidade que contém a chave privada. Se um contêiner de chave não existir, um será criado. Se nenhuma das opções sk - ou - sv for usada, um contêiner de chave chamado JoeSoft é criado por padrão.  
  
    2.  `-n` `subjectName`. Especifica o nome da entidade. A convenção é prefixar o nome de entidade com "CN =" para "Nome comum".  
  
    3.  `-iv` `issuerKeyFile`. Especifica o arquivo de chave privada do emissor.  
  
    4.  `-ic` `issuerCertFile`. Especifica o local do certificado do emissor.  
  
     Por exemplo, o comando a seguir cria um certificado assinado pelo `TempCA` certificado de autoridade raiz com um nome de assunto de `"CN=SignedByCA"` usando a chave privada do emissor.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalar um certificado no repositório de autoridades de certificação raiz confiável  
 Depois de criar um certificado autoassinado, você pode instalá-lo no repositório de autoridades de certificação raiz confiáveis. Todos os certificados são assinados com o certificado agora são confiáveis pelo computador. Por esse motivo, exclua o certificado do armazenamento assim que você não precisa mais dela. Quando você excluir este certificado de autoridade raiz, todos os outros certificados assinados com ele se tornar não autorizados. Certificados de autoridade raiz são simplesmente um mecanismo pelo qual um grupo de certificados pode ser definido conforme o necessário. Por exemplo, em aplicativos de ponto a ponto, há normalmente não precisa de uma autoridade raiz porque você confia simplesmente a identidade de um indivíduo por seu certificado fornecido.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Para instalar um certificado autoassinado em autoridades de certificação raiz confiáveis  
  
1.  Abra o snap-in de certificado. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Abra a pasta para armazenar o certificado, ou o **computador Local** ou **usuário atual**.  
  
3.  Abra o **autoridades de certificação raiz confiáveis** pasta.  
  
4.  Com o botão direito do **certificados** pasta e clique em **todas as tarefas**, em seguida, clique em **importação**.  
  
5.  Siga o assistente na tela instruções para importar o TempCa.cer para o armazenamento.  
  
## <a name="using-certificates-with-wcf"></a>Usar certificados com o WCF  
 Depois que você configurar os certificados temporários, você pode usá-los para desenvolver soluções WCF que especifique certificados como um tipo de credencial de cliente. Por exemplo, a configuração de XML a seguir especifica segurança de mensagem e um certificado como o tipo de credencial de cliente.  
  
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
  
 No arquivo de configuração para um cliente, use o seguinte XML para especificar que o certificado for encontrado no armazenamento do usuário e pode ser encontrado pesquisando o campo SubjectName para o valor "CohoWinery".  
  
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
  
 Para obter mais informações sobre como usar certificados no WCF, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Certifique-se de excluir qualquer certificados de autoridade raiz temporário do **autoridades de certificação raiz confiáveis** e **pessoal** pastas clicando duas vezes no certificado, em seguida, clicando em  **Excluir**.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
