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
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184902"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Como criar certificados X.509 que podem ser acessados pelo WCF
Para tornar um certificado X.509 acessível ao Windows Communication Foundation (WCF), o código do aplicativo deve especificar o nome e o local da loja de certificados. Em certas circunstâncias, a identidade do processo deve ter acesso ao arquivo que contém a chave privada associada ao certificado X.509. Para obter a chave privada associada a um certificado X.509 em uma loja de certificados, o WCF deve ter permissão para fazê-lo. Por padrão, apenas o proprietário e a conta do Sistema podem acessar a chave privada de um certificado.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Para tornar os certificados X.509 acessíveis ao WCF  
  
1. Dê a conta a qual o WCF está executando acesso de leitura ao arquivo que contém a chave privada associada ao certificado X.509.  
  
    1. Determine se o WCF requer acesso à chave privada para o certificado X.509.  
  
         A tabela a seguir detalha se uma chave privada deve estar disponível ao usar um certificado X.509.  
  
        |Uso do certificado X.509|Chave privada|  
        |---------------------------|-----------------|  
        |Assinando digitalmente uma mensagem SOAP de saída.|Sim|  
        |Verificando a assinatura de uma mensagem SOAP de entrada.|Não|  
        |Criptografando uma mensagem SOAP de saída.|Não|  
        |Descriptografando uma mensagem SOAP de entrada.|Sim|  
  
    2. Determine o local e o nome da loja de certificados em que o certificado é armazenado.  
  
         A loja de certificados em que o certificado é armazenado é especificada no código do aplicativo ou na configuração. Por exemplo, o exemplo a seguir especifica que `CurrentUser` o `My`certificado está localizado na loja de certificados nomeada .  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Determine onde a chave privada do certificado está localizada no computador usando a ferramenta [FindPrivateKey.](../../../../docs/framework/wcf/samples/findprivatekey.md)  
  
         A ferramenta [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) requer o nome da loja de certificados, a localização da loja de certificados e algo que identifica exclusivamente o certificado. A ferramenta aceita o nome do assunto do certificado ou sua impressão digital como um identificador único. Para obter mais informações sobre como determinar a impressão digital de um certificado, consulte [Como: Recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         O exemplo de código a seguir usa a ferramenta [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) para `My` determinar `CurrentUser` a localização `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`da chave privada de um certificado na loja com uma impressão digital de .  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Determine a conta em que o WCF está sendo executado.  
  
         A tabela a seguir detalha a conta a qual o WCF está executando para um determinado cenário.  
  
        |Cenário|Identidade do processo|  
        |--------------|----------------------|  
        |Cliente (aplicativo de console ou WinForms).|Atualmente logado no usuário.|  
        |Serviço que é auto-hospedado.|Atualmente logado no usuário.|  
        |Serviço hospedado no IIS 6.0 (Windows Server 2003) ou IIS 7.0 (Windows Vista).|SERVIÇO DE REDE|  
        |Serviço hospedado no IIS 5.X (Windows XP).|Controlado pelo `<processModel>` elemento no arquivo Machine.config. A conta padrão é ASPNET.|  
  
    5. Conceder acesso de leitura ao arquivo que contém a chave privada da conta em que o WCF está executando, usando uma ferramenta como icacls.exe.  
  
         O exemplo do código a seguir emite a lista de controle de acesso discricionário (DACL) para o arquivo especificado para conceder à conta DO SERVIÇO DE REDE acesso lido (:R) ao arquivo.  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Confira também

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Como recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
