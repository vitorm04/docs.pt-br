---
title: Como recuperar metadados e implementar um serviço compatível
ms.date: 03/30/2017
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
ms.openlocfilehash: 0a13d504b1c7c38ec13fee58c36913a75119271b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184854"
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Como recuperar metadados e implementar um serviço compatível
Muitas vezes, a mesma pessoa não projeta e implementa serviços. Em ambientes onde os aplicativos interoperacionais são importantes, os contratos podem ser projetados ou descritos no Web Services Description Language (WSDL) e um desenvolvedor deve implementar um serviço que esteja em conformidade com o contrato fornecido. Você também pode querer migrar um serviço existente para o Windows Communication Foundation (WCF), mas preservar o formato do fio. Além disso, os contratos duplex exigem que os chamadores implementem um contrato de retorno de chamada também.  
  
 Nesses casos, você deve usar a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (ou uma ferramenta equivalente) para gerar uma interface de contrato de serviço em uma linguagem gerenciada que você pode implementar para cumprir os requisitos do contrato. Normalmente, a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) é usada para adquirir um contrato de serviço que é usado com uma fábrica de canais ou um tipo de cliente WCF, bem como com um arquivo de configuração do cliente que configura a vinculação e endereço corretos. Para usar o arquivo de configuração gerado, você deve alterá-lo em um arquivo de configuração de serviço. Você também pode precisar modificar o contrato de serviço.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Para recuperar dados e implementar um serviço compatível  
  
1. Use a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contra arquivos de metadados ou um ponto final de metadados para gerar um arquivo de código.  
  
2. Pesquise a parte do arquivo de código de saída que contém a interface de <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> interesse (caso haja mais de um) que esteja marcada com o atributo. O exemplo de código a seguir mostra as duas interfaces geradas pelo [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). A primeira`ISampleService`( ) é a interface de contrato de serviço que você implementa para criar um serviço compatível. O segundo`ISampleServiceChannel`( ) é uma interface auxiliar para uso <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> do cliente que estende tanto a interface do contrato de serviço quanto e é para uso em um aplicativo cliente.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3. Se o WSDL não especificar uma ação de resposta para todas <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> as operações, os contratos de operação gerados poderão ter a propriedade definida para o caractere curinga (*). Remova esta configuração de propriedade. Caso contrário, quando você implementa os metadados do contrato de serviço, os metadados não podem ser exportados para essas operações.  
  
4. Implemente a interface em uma classe e hospede o serviço. Por exemplo, [consulte Como implementar um contrato de serviço](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)ou veja uma implementação simples abaixo na seção Exemplo.  
  
5. No arquivo de configuração do cliente que a [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gera, altere a [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) seção de configuração>cliente para uma [ \<seção de configuração de serviços>.](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) (Para um exemplo de um arquivo de configuração de aplicativo cliente gerado, consulte a seguinte seção "Exemplo".)  
  
6. Dentro da `name` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção de configuração [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/services.md)>de serviços, crie um atributo na seção de configuração de>de serviços para a implementação do serviço.  
  
7. Defina `name` o atributo de serviço ao nome de configuração para a implementação do serviço.  
  
8. Adicione os elementos de configuração de ponto final que usam o contrato de serviço implementado à seção de configuração do serviço.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra a maioria de um arquivo de código gerado executando o [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) contra arquivos de metadados.  
  
 O código a seguir mostra:  
  
- A interface do contrato de serviço que, quando`ISampleService`implementada, cumpre com os requisitos contratuais ( ).  
  
- A interface auxiliar para uso do cliente que <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> estende tanto a interface`ISampleServiceChannel`do contrato de serviço quanto é para uso em um aplicativo cliente ( ).  
  
- A classe auxiliar <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> que se estende e é`SampleServiceClient`para uso em um aplicativo cliente ( ).  
  
- O arquivo de configuração gerado a partir do serviço.  
  
- Uma `ISampleService` simples implementação de serviço.  
  
- Uma conversão do arquivo de configuração do lado do cliente para uma versão do lado do serviço.  
  
[!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]

[!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]

[!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]

[!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]
  
## <a name="see-also"></a>Confira também

- [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
