---
title: 'Como: especificar uma associação de cliente no código'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: c95e30c65c6096140fca0c1241e76fbc7af4df3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929123"
---
# <a name="how-to-specify-a-client-binding-in-code"></a>Como: especificar uma associação de cliente no código
Neste exemplo, um cliente é criado para usar um serviço de Calculadora e a associação para esse cliente é especificada imperativa no código. O cliente acessa o `CalculatorService`, que implementa o `ICalculator` interface e o serviço e o cliente use o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 Este procedimento pressupõe que o serviço da calculadora está em execução. Para obter informações sobre o serviço, consulte [como: Especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Ele também usa o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente. A ferramenta gera o código do cliente para acessar o serviço.  
  
 O cliente é criado em duas partes. Svcutil.exe gera o `ClientCalculator` que implementa o `ICalculator` interface. Esse aplicativo cliente é construído, em seguida, construindo uma instância de `ClientCalculator` e, em seguida, especificando a ligação e o endereço para o serviço no código.  
  
 Para a cópia de origem deste exemplo, consulte o [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemplo.  
  
### <a name="to-specify-a-custom-binding-in-code"></a>Para especificar uma associação personalizada em código  
  
1. Use Svcutil.exe da linha de comando para gerar o código de metadados de serviço.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. O cliente gerado também contém a implementação do `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. Criar uma instância das `ClientCalculator` que usa o <xref:System.ServiceModel.BasicHttpBinding> de classe em um aplicativo cliente e, em seguida, chame as operações de serviço no endereço especificado.  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. Compile e execute o cliente.  
  
## <a name="see-also"></a>Consulte também

- [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
