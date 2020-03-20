---
title: Como especificar uma associação de cliente em código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 9be571d7be020aef546fdd7ec7cb7519a48ea350
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184050"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Como especificar uma associação de cliente em código
Neste exemplo, um cliente é criado para usar um serviço de calculadora e a vinculação para esse cliente é especificada imperativamente em código. O cliente acessa o `CalculatorService` `ICalculator` , que implementa a interface, <xref:System.ServiceModel.BasicHttpBinding> e tanto o serviço quanto o cliente usam a classe.  
  
 Este procedimento pressupõe que o serviço de calculadora está em execução. Para obter informações sobre a construção do serviço, consulte [Como: Especificar uma vinculação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md). Ele também usa a [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente. A ferramenta gera o código do cliente para acessar o serviço.  
  
 O cliente é construído em duas partes. Svcutil.exe gera `ClientCalculator` o que `ICalculator` implementa a interface. Esse aplicativo cliente é então construído construindo `ClientCalculator` uma instância e, em seguida, especificando a vinculação e o endereço para o serviço em código.  
  
 Para obter a cópia de origem deste exemplo, consulte a amostra [BasicBinding.](./samples/basicbinding.md)  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Para especificar uma vinculação personalizada em código  
  
1. Use Svcutil.exe da linha de comando para gerar código a partir de metadados de serviço.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. O cliente gerado contém `ICalculator` a interface que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. O cliente gerado também contém `ClientCalculator`a implementação do .  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Crie uma instância `ClientCalculator` do <xref:System.ServiceModel.BasicHttpBinding> que usa a classe em um aplicativo cliente e, em seguida, chame as operações de serviço no endereço especificado.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Compile e execute o cliente.  
  
## <a name="see-also"></a>Confira também

- [Usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
