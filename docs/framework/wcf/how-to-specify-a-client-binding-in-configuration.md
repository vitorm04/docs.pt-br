---
title: Como especificar uma associação de cliente em configuração
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: e2ea5a4b1c2ca9b661be5d4c653a3b5668bd26f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Como especificar uma associação de cliente em configuração
Neste exemplo, um aplicativo de console do cliente é criado para usar um serviço de cálculo e a associação para que o cliente é especificada declarativamente na configuração. O cliente acessa o `CalculatorService`, que implementa o `ICalculator` interface e o serviço e o cliente use o <xref:System.ServiceModel.BasicHttpBinding> classe.  
  
 O procedimento descrito assume que o serviço de cálculo é executada. Para obter informações sobre como criar o serviço, consulte [como: especificar uma associação de serviço na configuração](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md). Ele também usa o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente. A ferramenta gera o código de cliente e configuração para acessar o serviço.  
  
 O cliente é criado em duas partes. Svcutil.exe gera o `ClientCalculator` que implementa o `ICalculator` interface. Este aplicativo cliente é construído, criando uma instância de `ClientCalculator`.  
  
 Geralmente é a prática recomendada para especificar declarativamente a associação e as informações de endereço na configuração em vez de imperativa no código. Definir pontos de extremidade no código geralmente não é prático porque as associações e os endereços para um serviço implantado normalmente são diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Geralmente, informações sem o código de endereçamento e manter a associação permite que a alteração sem precisar recompilar ou reimplantar o aplicativo.  
  
 Você pode executar todas as seguintes etapas de configuração usando o [ferramenta Configuration Editor (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para a cópia de origem deste exemplo, consulte o [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) exemplo.  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Especificando uma associação na configuração de cliente  
  
1.  Use o Svcutil.exe da linha de comando para gerar o código de metadados de serviço.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  O cliente que é gerado contém o `ICalculator` interface que define o contrato de serviço que deve atender a implementação do cliente.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3.  O cliente gerado também contém a implementação de `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4.  Svcutil.exe também gera a configuração do cliente que usa o <xref:System.ServiceModel.BasicHttpBinding> classe. Ao usar o Visual Studio, nomeie esse arquivo App. config. Observe que o endereço e as informações de associação não estão especificados em qualquer lugar dentro da implementação do serviço. Além disso, o código não tem a ser gravado para recuperar informações do arquivo de configuração.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5.  Criar uma instância do `ClientCalculator` em um aplicativo e, em seguida, chamar as operações de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6.  Compile e execute o cliente.  
  
## <a name="see-also"></a>Consulte também  
 [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
