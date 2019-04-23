---
title: 'Como: configurar uma porta com um certificado SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: d709123895f361c1d2268a218b4163c8d195e1b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59345580"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Como: configurar uma porta com um certificado SSL
Ao criar um serviço Windows Communication Foundation (WCF) auto-hospedado com o <xref:System.ServiceModel.WSHttpBinding> classe que usa segurança de transporte, você também deve configurar uma porta com um certificado X.509. Se você estiver criando um serviço auto-hospedado, você poderá hospedá-lo serviço no IIS (Serviços de Informações da Internet). Para obter mais informações, consulte [segurança de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Para configurar uma porta, a ferramenta usada depende do sistema operacional que está sendo executado no computador.  
  
 Se estiver executando o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou o [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe. Com o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] essa ferramenta é instalada. Com o [!INCLUDE[wxp](../../../../includes/wxp-md.md)], você pode baixar a ferramenta em [ferramentas de suporte do Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606). Para obter mais informações, consulte [visão geral de HTTPCFG&lt;2}&lt;1](https://go.microsoft.com/fwlink/?LinkId=88605). O [documentação de ferramentas de suporte do Windows](https://go.microsoft.com/fwlink/?LinkId=94840) explica a sintaxe da ferramenta Httpcfg.exe.  
  
 Se estiver executando o [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe que já está instalada.  
  
 Este tópico descreve como executar vários procedimentos:  
  
-   Determinar a configuração atual da porta de um computador.  
  
-   Obter impressão digital de um certificado (necessário para os próximos dois procedimentos).  
  
-   Associar um certificado SSL a uma configuração de porta.  
  
-   Associar um certificado SSL a uma configuração de porta e dar suporte a certificados do cliente.  
  
-   Excluir um certificado SSL de um número de porta.  
  
 Observe que a modificação de certificados armazenados no computador requer privilégios administrativos.  
  
### <a name="to-determine-how-ports-are-configured"></a>Para determinar como as portas estão configuradas  
  
1. Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe para exibir a configuração atual da porta, usando o **consulta** e **ssl** alterna, conforme mostrado no exemplo a seguir.  
  
    ```  
    httpcfg query ssl  
    ```  
  
2. No [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe para exibir a configuração atual da porta, conforme mostrado no exemplo a seguir.  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Para obter a impressão digital de um certificado  
  
1. Use o snap-in do MMC dos Certificados para localizar um certificado X.509 cuja finalidade seja a autenticação de cliente. Para obter mais informações, confira [Como: Exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Para acessar a impressão digital do certificado. Para obter mais informações, confira [Como: Recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Copie a impressão digital do certificado em um editor de texto, como o Bloco de Notas.  
  
4. Remova todos os espaços entre os caracteres hexadecimais. Uma maneira de fazer isso é usar o recurso localizar e substituir do editor de texto e substituir cada espaço com um caractere nulo.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Para associar um certificado SSL a um número de porta.  
  
1. No [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou no [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe no modo “set” no repositório SSL para associar o certificado a um número de porta. A ferramenta usa a impressão digital para identificar o certificado, conforme mostrado no exemplo o seguir.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   O **-i** switch tem a sintaxe `IP`:`port` e instrui a ferramenta para definir o certificado para a porta 8012 do computador. Opcionalmente, os quatro zeros que precedem o número também podem ser substituídos pelo endereço IP real do computador.  
  
    -   O **-h** opção especifica a impressão digital do certificado.  
  
2. No [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe, conforme mostrado no exemplo a seguir.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   O **certhash** parâmetro especifica a impressão digital do certificado.  
  
    -   O **ipport** parâmetro especifica o endereço IP e porta e funções exatamente como o **-i** switch da ferramenta Httpcfg.exe descrita.  
  
    -   O **appid** parâmetro é um GUID que pode ser usado para identificar o aplicativo proprietário.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Para associar um certificado SSL a um número de porta e dar suporte a certificados do cliente  
  
1. No [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou no [!INCLUDE[wxp](../../../../includes/wxp-md.md)], para dar suporte aos clientes que se autenticam com os certificados X.509 na camada de transporte, siga o procedimento anterior, mas inclua um parâmetro adicional de linha de comando em HttpCfg.exe, conforme mostrado no exemplo a seguir.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     O **-f** switch tem a sintaxe `n` onde n é um número entre 1 e 7. Um valor de 2, conforme mostrado no exemplo anterior, permite certificados do cliente na camada de transporte. Um valor de 3 permite certificados do cliente e mapeia esses certificados para uma conta do Windows. Consulte a Ajuda do HttpCfg.exe para obter o comportamento de outros valores.  
  
2. No [!INCLUDE[wv](../../../../includes/wv-md.md)], para dar suporte aos clientes que se autenticam com os certificados X.509 na camada de transporte, siga o procedimento anterior, mas com um parâmetro adicional, conforme mostrado no exemplo a seguir.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Para excluir um certificado SSL de um número de porta  
  
1. Use a ferramenta HttpCfg.exe ou Netsh.exe para ver as portas e as impressões digitais de todas as associações no computador. Para imprimir informações em disco, use o caractere de redirecionamento ">", conforme mostrado no exemplo a seguir.  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2. Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe com o **excluir** e **ssl** palavras-chave. Use o **-i** para especificar o `IP`:`port` número e o **-h** para especificar a impressão digital.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. No [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe, conforme mostrado no exemplo a seguir.  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Exemplo  
 O código a seguir mostra como criar um serviço auto-hospedado usando o conjunto de classes <xref:System.ServiceModel.WSHttpBinding> para segurança no transporte. Ao criar um aplicativo, especifique o número da porta no endereço.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Segurança de transporte de HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
