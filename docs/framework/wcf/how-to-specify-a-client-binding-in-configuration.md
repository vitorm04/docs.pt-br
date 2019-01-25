---
title: 'Como: Especificar uma associação de cliente na configuração'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 2441b307961079c28e114b4fed69c252ff42e0d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606381"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Como: Especificar uma associação de cliente na configuração
Neste exemplo, um aplicativo de console do cliente é criado para usar um serviço de Calculadora e a associação para que o cliente é especificada declarativamente na configuração. O cliente acessa o `CalculatorService`, que implementa o `ICalculator` interface e o serviço e o cliente use o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 O procedimento descrito pressupõe que o serviço da calculadora está em execução. Para obter informações sobre como criar o serviço, consulte [como: Especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Ele também usa o [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) que o Windows Communication Foundation (WCF) oferece para gerar automaticamente os componentes do cliente. A ferramenta gera o código do cliente e a configuração de acesso ao serviço.  
  
 O cliente é criado em duas partes. Svcutil.exe gera o `ClientCalculator` que implementa o `ICalculator` interface. Esse aplicativo cliente é construído, em seguida, construindo uma instância de `ClientCalculator`.  
  
 Ele geralmente é a prática recomendada para especificar declarativamente as informações de endereço e associação na configuração em vez de imperativa no código. Definir pontos de extremidade no código geralmente não é prático porque as associações e endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. De modo geral, informações fora do código de endereçamento e manter a associação permite que eles alterem os sem ter que recompilar ou reimplantar o aplicativo.  
  
 Você pode executar todas as seguintes etapas de configuração usando o [ferramenta de Editor de configuração (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para a cópia de origem deste exemplo, consulte o [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemplo.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Especificando um ligação na configuração do cliente  
  
1.  Use Svcutil.exe da linha de comando para gerar o código de metadados de serviço.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  O cliente gerado também contém a implementação do `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  Svcutil.exe também gera a configuração do cliente que usa o <xref:System.ServiceModel.BasicHttpBinding> classe. Ao usar o Visual Studio, nomeie esse arquivo App. config. Observe que o endereço e informações de associação não estão especificados em qualquer lugar dentro da implementação do serviço. Além disso, código não precisa ser escrita para recuperar essas informações do arquivo de configuração.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  Criar uma instância das `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  Compile e execute o cliente.  
  
## <a name="see-also"></a>Consulte também
- [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
