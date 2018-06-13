---
title: Como criar certificados X.509 que podem ser acessados pelo WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: cd13eae0a72ceaf5abfb93dfe84a53cfc3c8dec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493700"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Como criar certificados X.509 que podem ser acessados pelo WCF
Para tornar um certificado x. 509 acessíveis para o Windows Communication Foundation (WCF), o código do aplicativo deve especificar o nome do repositório de certificado e o local. Em determinadas circunstâncias, a identidade do processo deve ter acesso ao arquivo que contém a chave privada associada ao certificado x. 509. Para obter a chave privada associada a um certificado x. 509 em um repositório de certificados, o WCF deve ter permissão para fazer isso. Por padrão, somente o proprietário e a conta do sistema podem acessar a chave privada de um certificado.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Para disponibilizar os certificados x. 509 para o WCF  
  
1.  Conceda à conta sob a qual WCF está executando o acesso de leitura para o arquivo que contém a chave privada associada ao certificado x. 509.  
  
    1.  Determine se o WCF requer acesso de leitura à chave privada do certificado x. 509.  
  
         A tabela a seguir fornece detalhes sobre se uma chave privada deve estar disponível ao usar um certificado x. 509.  
  
        |Uso de certificados x. 509|Chave privada|  
        |---------------------------|-----------------|  
        |Assinar digitalmente uma mensagem SOAP de saída.|Sim|  
        |Verificar a assinatura de uma mensagem SOAP de entrada.|Não|  
        |Criptografar uma mensagem SOAP de saída.|Não|  
        |Descriptografar uma mensagem SOAP de entrada.|Sim|  
  
    2.  Determine o repositório de certificados local e o nome no qual o certificado é armazenado.  
  
         O repositório de certificados no qual o certificado é armazenado é especificado no código do aplicativo ou na configuração. Por exemplo, o exemplo a seguir especifica que o certificado está localizado no `CurrentUser` repositório de certificados denominado `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Determinar onde a chave privada do certificado está localizada no computador usando o [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) ferramenta.  
  
         O [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) ferramenta requer o nome do repositório de certificados, repositório de certificados local e algo que identifica exclusivamente o certificado. A ferramenta aceita o nome da entidade do certificado ou sua impressão digital como um identificador exclusivo. Para obter mais informações sobre como determinar a impressão digital de um certificado, consulte [como: recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         O seguinte exemplo de código usa o [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool para determinar o local da chave privada de um certificado no `My` armazenar em `CurrentUser` com uma impressão digital de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  Determine a conta que o WCF está sendo executado.  
  
         A tabela a seguir fornece detalhes sobre a conta sob a qual o WCF está em execução para um determinado cenário.  
  
        |Cenário|Identidade de processo|  
        |--------------|----------------------|  
        |Cliente (console ou aplicativos WinForms).|Usuário conectado no momento.|  
        |Serviço auto-hospedado.|Usuário conectado no momento.|  
        |Serviço hospedado no IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) ou IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|SERVIÇO DE REDE|  
        |Serviço que é hospedado no IIS 5. x ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Controlado pelo `<processModel>` elemento no arquivo Machine. config. A conta padrão é ASPNET.|  
  
    5.  Conceder acesso de leitura para o arquivo que contém a chave privada para a conta que o WCF está em execução, usando uma ferramenta como cacls.exe.  
  
         Edições de exemplo de código a seguir (/ E) a lista de controle de acesso (ACL) para o arquivo especificado conceder (/ G) a conta de serviço de rede de leitura (: R) acesso ao arquivo.  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Consulte também  
 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [Como recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
