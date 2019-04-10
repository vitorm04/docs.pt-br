---
title: 'Como: criar certificados X.509 que podem ser acessados pelo WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: 0177533f11b7dfa6c2561f1f519eacf8073bcd45
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331072"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Como: criar certificados X.509 que podem ser acessados pelo WCF
Para disponibilizar um certificado X.509 para o Windows Communication Foundation (WCF), o código do aplicativo deve especificar o nome do repositório de certificado e o local. Em determinadas circunstâncias, a identidade do processo deve ter acesso ao arquivo que contém a chave privada associada ao certificado x. 509. Para obter a chave privada associada com um certificado x. 509 em um repositório de certificados, o WCF deve ter permissão para fazer isso. Por padrão, somente o proprietário e a conta do sistema podem acessar a chave privada de um certificado.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Para criar certificados X.509 acessíveis para o WCF  
  
1. Conceda à conta sob a qual o WCF está executando o acesso de leitura para o arquivo que contém a chave privada associada ao certificado x. 509.  
  
    1.  Determine se o WCF requer acesso de leitura à chave privada do certificado X.509.  
  
         A tabela a seguir fornece detalhes sobre se uma chave privada deve estar disponível ao usar um certificado x. 509.  
  
        |Uso de certificados X.509|chave privada|  
        |---------------------------|-----------------|  
        |Assinar digitalmente uma mensagem SOAP de saída.|Sim|  
        |Verificar a assinatura de uma mensagem SOAP de entrada.|Não|  
        |Criptografar uma mensagem SOAP de saída.|Não|  
        |Descriptografando uma mensagem SOAP de entrada.|Sim|  
  
    2.  Determine o nome no qual o certificado é armazenado e o repositório de certificados local.  
  
         O repositório de certificados na qual o certificado é armazenado é especificado no código do aplicativo ou na configuração. Por exemplo, o exemplo a seguir especifica que o certificado está localizado na `CurrentUser` repositório de certificados denominado `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Determinar onde a chave privada do certificado está localizada no computador usando o [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) ferramenta.  
  
         O [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) ferramenta requer o nome do repositório de certificados, repositório de certificados local e algo que identifica exclusivamente o certificado. A ferramenta aceita o nome da entidade do certificado ou sua impressão digital como um identificador exclusivo. Para obter mais informações sobre como determinar a impressão digital de um certificado, consulte [como: Recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         O seguinte exemplo de código usa o [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) tool para determinar o local da chave privada de um certificado na `My` armazenar no `CurrentUser` com uma impressão digital de `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  Determine a conta que o WCF está sendo executado.  
  
         A tabela a seguir fornece detalhes sobre a conta sob a qual o WCF está sendo executado para um determinado cenário.  
  
        |Cenário|Identidade do processo|  
        |--------------|----------------------|  
        |Cliente (console ou WinForms aplicativo).|Usuário atualmente conectado.|  
        |Serviço auto-hospedado.|Usuário atualmente conectado.|  
        |Serviço que é hospedado no IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) ou o IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|SERVIÇO DE REDE|  
        |Serviço que é hospedado no IIS 5. x ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Controlado pelo `<processModel>` elemento no arquivo Machine. config. A conta padrão é ASPNET.|  
  
    5.  Conceder acesso de leitura para o arquivo que contém a chave privada para a conta que o WCF está em execução, usando uma ferramenta como icacls.exe.  
  
         O exemplo de código a seguir edita a lista de controle de acesso discricionário (DACL) para o arquivo especificado conceder a leitura da conta de serviço de rede (: R) acesso ao arquivo.  
  
        ```  
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Consulte também

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Como: recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
