---
title: Encaminhamento de tipo no Common Language Runtime
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32dad99e8d5caa7d88fa302a1bea8b83847bfde3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Encaminhamento de tipo no Common Language Runtime
O encaminhamento de tipo permite que você mova um tipo para outro assembly sem ter que recompilar os aplicativos que usam o assembly original.  
  
 Por exemplo, suponha que um aplicativo use a classe `Example` em um assembly chamado `Utility.dll`. Os desenvolvedores de `Utility.dll` podem decidir refatorar o assembly e, durante o processo, podem mover a classe `Example` para outro conjunto. Se a versão antiga do `Utility.dll` for substituída pela nova versão do `Utility.dll` e por seu assembly complementar, o aplicativo que usa a classe `Example` falhará porque não foi possível localizar a classe `Example` na nova versão do `Utility.dll`.  
  
 Os desenvolvedores de `Utility.dll` pode evitar isso encaminhando solicitações para a classe `Example`, usando o atributo <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>. Se o atributo tiver sido aplicado à nova versão do `Utility.dll`, as solicitações para a classe `Example` são encaminhadas ao assembly que agora contém a classe. O aplicativo existente continua a funcionar normalmente, sem recompilação.  
  
> [!NOTE]
>  No .NET Framework versão 2.0, você não pode encaminhar os tipos de assemblies escritos em Visual Basic. No entanto, um aplicativo escrito em Visual Basic pode consumir tipos encaminhados. Ou seja, se o aplicativo usar um assembly de código em C# ou C++, e um tipo desse assembly for encaminhado para outro assembly, o aplicativo em Visual Basic poderá usar o tipo encaminhado.  
  
## <a name="forwarding-types"></a>Encaminhamento de tipos  
 Há quatro etapas para encaminhar um tipo:  
  
1.  Mova o código-fonte para o tipo do assembly original para o conjunto de destino.  
  
2.  No assembly em que o tipo é usado para ser localizado, adicione um <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para o tipo que foi movido. O código a seguir mostra o atributo para um tipo chamado `Example` que foi movido.  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  Compile o assembly que agora contém o tipo.  
  
4.  Recompile o assembly onde o tipo estava localizado, com uma referência ao assembly que agora contém o tipo. Por exemplo, se você estiver compilando um arquivo em C# na linha de comando, use a opção [/reference (opções do compilador em C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) para especificar o assembly que contém o tipo. Em C++, use a diretiva [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) no arquivo de origem para especificar o assembly que contém o tipo.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [Encaminhamento de tipo (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)  
 [Diretiva #using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
