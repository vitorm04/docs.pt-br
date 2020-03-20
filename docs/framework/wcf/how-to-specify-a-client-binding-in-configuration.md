---
title: Como especificar uma associação de cliente em configuração
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184046"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Como especificar uma associação de cliente em configuração
Neste exemplo, um aplicativo de console cliente é criado para usar um serviço de calculadora, e a vinculação para esse cliente é especificada declarativamente na configuração. O cliente acessa o `CalculatorService` `ICalculator` , que implementa a interface, <xref:System.ServiceModel.BasicHttpBinding> e tanto o serviço quanto o cliente usam a classe.  
  
 O procedimento descrito pressupõe que o serviço de calculadora está em execução. Para obter informações sobre como construir o serviço, consulte [Como: Especificar uma vinculação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md). Ele também usa a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente. A ferramenta gera o código e configuração do cliente para acessar o serviço.  
  
 O cliente é construído em duas partes. Svcutil.exe gera `ClientCalculator` o que `ICalculator` implementa a interface. Este aplicativo cliente é então construído construindo `ClientCalculator`uma instância de .  
  
 Geralmente é a melhor prática para especificar as informações de vinculação e endereço declarativamente na configuração, em vez de imperativamente em código. Definir pontos finais no código geralmente não é prático porque as vinculações e endereços de um serviço implantado são tipicamente diferentes daqueles usados enquanto o serviço está sendo desenvolvido. De forma mais geral, manter as informações de vinculação e endereçamento fora do código permite que eles mudem sem ter que recompilar ou reimplantar o aplicativo.  
  
 Você pode executar todas as seguintes etapas de configuração usando a [Ferramenta de Editor de Configuração (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para obter a cópia de origem deste exemplo, consulte a amostra [BasicBinding.](./samples/basicbinding.md)  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Especificando uma vinculação do cliente na configuração  
  
1. Use Svcutil.exe da linha de comando para gerar código a partir de metadados de serviço.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. O cliente gerado contém `ICalculator` a interface que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. O cliente gerado também contém `ClientCalculator`a implementação do .  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe também gera a configuração <xref:System.ServiceModel.BasicHttpBinding> para o cliente que usa a classe. Ao usar o Visual Studio, nomeie este arquivo App.config. Observe que o endereço e as informações de vinculação não são especificados em nenhum lugar dentro da implementação do serviço. Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. Crie uma instância `ClientCalculator` do em um aplicativo e, em seguida, chame as operações de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Compile e execute o cliente.  
  
## <a name="see-also"></a>Confira também

- [Usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
