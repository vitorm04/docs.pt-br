---
title: 'Como: recuperar metadados e implementar um serviço em conformidade'
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 2ddc50e2851217002c825163761855d649b56db1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095965"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Como: recuperar metadados e implementar um serviço em conformidade
Muitas vezes, a mesma pessoa não projetar e implementar serviços. Em ambientes em que os aplicativos interoperacionais são importantes, contratos podem ser criados ou descritos na descrição de linguagem WSDL (Web Services) e um desenvolvedor deve implementar um serviço que está em conformidade com o contrato fornecido. Talvez você queira migrar um serviço existente para o Windows Communication Foundation (WCF), mas preservar o formato de conexão. Além disso, os contratos duplex exigem chamadores implementar um contrato de retorno de chamada também.  
  
 Nesses casos, você deve usar o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (ou uma ferramenta equivalente) para gerar uma interface de contrato de serviço em uma linguagem gerenciada que você pode implementar para cumprir os requisitos das contrato. Normalmente o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) é usado para adquirir um contrato de serviço que é usado com uma fábrica de canais ou um tipo de cliente do WCF, bem como com um arquivo de configuração de cliente que configura a associação correta e o endereço. Para usar o arquivo de configuração gerado, você deve alterá-lo em um arquivo de configuração de serviço. Você também precisará modificar o contrato de serviço.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Para recuperar dados e implementar um serviço compatível  
  
1.  Use o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) em relação a arquivos de metadados ou um ponto de extremidade de metadados para gerar um arquivo de código.  
  
2.  Pesquisa por uma parte do código do arquivo de saída que contém a interface de interesse (no caso, não há mais de uma) que é marcado com o <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atributo. O exemplo de código a seguir mostra as duas interfaces geradas pelo [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). O primeiro (`ISampleService`) é a interface de contrato de serviço que você pode implementar para criar um serviço em conformidade. A segunda (`ISampleServiceChannel`) é uma interface do auxiliar para uso do cliente que estende tanto a interface de contrato de serviço e <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> e é para uso em um aplicativo cliente.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  Se o WSDL não especificar uma ação de resposta para todas as operações, os contratos de operação gerados podem ter o <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> propriedade definida como o caractere curinga (*). Remova a configuração dessa propriedade. Caso contrário, quando você implementa os metadados do contrato de serviço, os metadados não podem ser exportado para essas operações.  
  
4.  Implementar a interface em uma classe e hospedar o serviço. Para obter um exemplo, consulte [ Implementar um contrato de serviço](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), ou veja uma implementação simples abaixo na seção de exemplo.  
  
5.  Na configuração do cliente de arquivos que o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gera, altere o [ \<cliente >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) seção de configuração para um [ \<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção de configuração. (Para obter um exemplo de um arquivo de configuração de aplicativo de cliente gerado, consulte a seção "Exemplo" a seguir).  
  
6.  Dentro do [ \<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuração seção, crie um `name` atributo no [ \<serviços >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção de configuração para seu serviço implementação.  
  
7.  Defina o serviço `name` de atributo para o nome de configuração para sua implementação de serviço.  
  
8.  Adicione os elementos de configuração de ponto de extremidade que usam o contrato de serviço implementada para a seção de configuração de serviço.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra a maior parte de um arquivo de código gerado pela execução de [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) em relação aos arquivos de metadados.  
  
 O código a seguir mostra:  
  
-   O contrato de serviço de interface que, quando implementada, está em conformidade com os requisitos de contrato (`ISampleService`).  
  
-   A interface do auxiliar para uso do cliente que estende tanto a interface de contrato de serviço e <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> e é para uso em um aplicativo cliente (`ISampleServiceChannel`).  
  
-   A classe auxiliar que estende <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> e é para uso em um aplicativo cliente (`SampleServiceClient`).  
  
-   O arquivo de configuração gerado pelo serviço.  
  
-   Um simples `ISampleService` implementação do serviço.  
  
-   Uma conversão do arquivo de configuração do lado do cliente para uma versão do lado do serviço.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Consulte também

- [Ferramenta Utilitário de Metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
