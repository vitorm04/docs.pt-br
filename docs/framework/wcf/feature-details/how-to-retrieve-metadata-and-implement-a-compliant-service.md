---
title: "Como recuperar metadados e implementar um serviço compatível"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6f3a2b9-c8aa-4b0b-832c-ec2927bf1163
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 33090cd855aa41607f6d330d695f24a6f60197d6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-retrieve-metadata-and-implement-a-compliant-service"></a>Como recuperar metadados e implementar um serviço compatível
Geralmente, a mesma pessoa não projetar e implementar serviços. Em ambientes com aplicativos interoperacionais importantes, contratos podem ser criados ou descritos no WSDL Web Services Description Language () e um desenvolvedor deve implementar um serviço que está em conformidade com o contrato fornecido. Talvez você queira migrar um serviço existente para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mas preservar o formato de transmissão. Além disso, os contratos duplex exigem chamadores implementar um contrato de retorno de chamada também.  
  
 Nesses casos, você deve usar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) (ou uma ferramenta equivalente) para gerar uma interface de contrato de serviço em uma linguagem gerenciada que você pode implementar para atender aos requisitos de contrato. Normalmente o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) é usado para adquirir um contrato de serviço que é usado com uma fábrica de canais ou um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] assim como um arquivo de configuração de cliente que define o tipo de cliente do endereço e a associação correta. Para usar o arquivo de configuração gerado, você deve alterar para um arquivo de configuração do serviço. Você também precisará modificar o contrato de serviço.  
  
### <a name="to-retrieve-data-and-implement-a-compliant-service"></a>Para recuperar dados e implementar um serviço compatível  
  
1.  Use o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) em arquivos de metadados ou um ponto de extremidade de metadados para gerar um arquivo de código.  
  
2.  Pesquise a parte do código do arquivo de saída que contém a interface de interesse (no caso, há mais de uma) que é marcado com o <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> atributo. O exemplo de código a seguir mostra as duas interfaces geradas por [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). O primeiro (`ISampleService`) é a interface de contrato de serviço que você pode implementar para criar um serviço compatível. A segunda (`ISampleServiceChannel`) é uma interface de auxiliar para uso do cliente que se estende a interface de contrato de serviço e <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> e é para uso em um aplicativo cliente.  
  
     [!code-csharp[ClientProxyCodeSample#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#2)]  
  
3.  Se o WSDL não especificar uma ação de resposta para todas as operações, os contratos de operação gerado podem ter o <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> propriedade definida como o caractere curinga (*). Remova a configuração dessa propriedade. Caso contrário, quando você implementa os metadados do contrato de serviço, os metadados não podem ser exportado para essas operações.  
  
4.  Implementa a interface em uma classe e o serviço de host. Para obter um exemplo, consulte [como: implementar um contrato de serviço](../../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md), ou consulte uma implementação simples abaixo na seção de exemplo.  
  
5.  Na configuração do cliente do arquivo que o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) gera, alterar o [ \<cliente >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) seção de configuração para um [ \<services >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção de configuração. (Para obter um exemplo de um arquivo de configuração do aplicativo cliente gerada, consulte a seção "Exemplo" a seguir).  
  
6.  Dentro de [ \<serviços >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) configuração seção, crie um `name` atributo no [ \<serviços >](../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção de configuração para o serviço implementação.  
  
7.  Configurar o serviço de `name` de atributo para o nome de configuração para a implementação do serviço.  
  
8.  Adicione os elementos de configuração de ponto de extremidade que usam o contrato de serviço implementado para a seção de configuração de serviço.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra a maior parte de um arquivo de código gerado pela execução de [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) em arquivos de metadados.  
  
 O código a seguir mostra:  
  
-   Interface de contrato de serviço que, quando implementada, está em conformidade com os requisitos de contrato (`ISampleService`).  
  
-   A interface do auxiliar para uso do cliente que se estende a interface de contrato de serviço e <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> e é para uso em um aplicativo cliente (`ISampleServiceChannel`).  
  
-   A classe auxiliar que estende o <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> e é para uso em um aplicativo cliente (`SampleServiceClient`).  
  
-   O arquivo de configuração gerado do serviço.  
  
-   Um simples `ISampleService` implementação do serviço.  
  
-   Uma conversão do arquivo de configuração do lado do cliente para uma versão do lado do serviço.  
  
 [!code-csharp[ClientProxyCodeSample#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/proxycode.cs#1)]    
 [!code-xml[ClientProxyCodeSample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/client.exe.config#10)]     
 [!code-csharp[ClientProxyCodeSample#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.cs#5)]    
 [!code-xml[ClientProxyCodeSample#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/clientproxycodesample/cs/hostapplication.exe.config#20)]    
  
## <a name="see-also"></a>Consulte também  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) [Ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)]
