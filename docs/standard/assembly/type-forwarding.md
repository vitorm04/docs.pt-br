---
title: Encaminhamento de tipo no Common Language Runtime
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160359"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a>Encaminhamento de tipo no Common Language Runtime
O encaminhamento de tipo permite que você mova um tipo para outro assembly sem ter que recompilar os aplicativos que usam o assembly original.  
  
 Por exemplo, suponha `Example` que um aplicativo use a classe em um conjunto chamado *Utility.dll*. Os desenvolvedores do *Utility.dll* podem decidir refatorar a montagem, `Example` e no processo eles podem mover a classe para outra montagem. Se a versão antiga do *Utility.dll* for substituída pela nova versão do *Utility.dll* e seu conjunto companheiro, o aplicativo que usa a `Example` classe falhará porque não consegue localizar a `Example` classe na nova versão do *Utility.dll*.  
  
 Os desenvolvedores do *Utility.dll* podem evitar isso `Example` encaminhando <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> solicitações para a classe, usando o atributo. Se o atributo tiver sido aplicado à nova versão do `Example` *Utility.dll,* as solicitações para a classe serão encaminhadas para a montagem que agora contém a classe. O aplicativo existente continua a funcionar normalmente, sem recompilação.  
  
> [!NOTE]
> No .NET Framework versão 2.0, você não pode encaminhar os tipos de assemblies escritos em Visual Basic. No entanto, um aplicativo escrito em Visual Basic pode consumir tipos encaminhados. Ou seja, se o aplicativo usar um assembly de código em C# ou C++, e um tipo desse assembly for encaminhado para outro assembly, o aplicativo em Visual Basic poderá usar o tipo encaminhado.  
  
## <a name="forward-types"></a>Tipos avançados  
 Há quatro etapas para encaminhar um tipo:  
  
1. Mova o código-fonte para o tipo do assembly original para o conjunto de destino.  

2. No assembly em que o tipo é usado para ser localizado, adicione um <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para o tipo que foi movido. O código a seguir mostra o atributo para um tipo chamado `Example` que foi movido.  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. Compile o assembly que agora contém o tipo.  

4. Recompile o assembly onde o tipo estava localizado, com uma referência ao assembly que agora contém o tipo. Por exemplo, se você estiver compilando um arquivo C# da linha de comando, use a opção [-reference (C# compilor options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) para especificar o conjunto que contém o tipo. Em C++, use a diretiva [#using](/cpp/preprocessor/hash-using-directive-cpp) no arquivo de origem para especificar o assembly que contém o tipo.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [Encaminhamento de tipo (C++/CLI)](/cpp/windows/type-forwarding-cpp-cli)
- [diretiva #using](/cpp/preprocessor/hash-using-directive-cpp)
