---
title: Como referenciar um assembly de nome forte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: aa46bfdfe42dca9509e39d4b6218473aa00a1877
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-reference-a-strong-named-assembly"></a>Como referenciar um assembly de nome forte
O processo para referenciar tipos ou recursos em um assembly de nome forte é normalmente transparente. Você pode fazer a referência no tempo de compilação (vinculação inicial) ou no tempo de execução.  
  
 Uma referência de tempo de compilação ocorre quando você indica para o compilador que seu assembly faz referência explícita a outro assembly. Quando você usa a referência no tempo de compilação, o compilador obtém automaticamente a chave pública do assembly com nome forte direcionado e o coloca na referência de assembly do assembly que está sendo compilado.  
  
> [!NOTE]
>  Assembly de nome forte só pode usar tipos de outros assemblies de nome forte. Caso contrário, a segurança do assembly de nome forte estaria comprometida.  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>Para fazer uma referência no tempo de compilação a um assembly de nome forte  
  
1.  No prompt de comando, digite o seguinte comando:  
  
     \<*comando do compilador*> **/reference:**\<*nome do assembly*>  
  
     Nesse comando, o *comando do compilador* é o comando do compilador para a linguagem que você está usando, e *nome do assembly* é o nome do assembly de nome forte que está sendo referenciado. Você também pode usar outras opções de compilador, como a opção **/t:library** para criar um assembly de biblioteca.  
  
 O exemplo a seguir cria um assembly chamado `myAssembly.dll` que faz referência a um assembly de nome forte chamado `myLibAssembly.dll` de um módulo de código chamado `myAssembly.cs`.  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>Para fazer uma referência no tempo de execução a um assembly de nome forte  
  
1.  Quando você faz uma referência de tempo de execução a um assembly de nome forte (por exemplo, usando o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> ou o <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName>), você deve usar o nome de exibição do assembly de nome forte referenciado. A sintaxe de um nome de exibição é a seguinte:  
  
     \<*nome do assembly*>**,** \<*número da versão*>**,** \<*cultura*>**,** \<*token de chave pública*>  
  
     Por exemplo:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     Neste exemplo, `PublicKeyToken` é a forma hexadecimal do token de chave pública. Se não houver valor de cultura, use `Culture=neutral`.  
  
 O exemplo de código a seguir mostra como usar essas informações com o método <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>.  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)] [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)] [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 Você pode imprimir o formato hexadecimal da chave pública e do token de chave pública para um assembly específico usando o seguinte comando [Nome Forte (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md):  
  
 **sn -Tp \<** *assembly* **>**  
  
 Se você tiver um arquivo de chave pública, use o comando a seguir (observe a diferença no caso da opção de linha de comando):  
  
 **sn -tp \<** *assembly* **>**  
  
## <a name="see-also"></a>Consulte também  
 [Criar e usar assemblies de nomes fortes](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)

