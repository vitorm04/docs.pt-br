---
title: "Como compilar um assembly de arquivo único | Microsoft Docs"
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
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0ddf25f1d588c0972381a54ee0da4b35e3c0dc33
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="how-to-build-a-single-file-assembly"></a>Como compilar um assembly de arquivo único
Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md). Você pode usar compiladores de linha de comando ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] para criar um assembly de arquivo único. Por padrão, o compilador cria um arquivo do assembly com uma extensão de .exe.  
  
> [!NOTE]
> O  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] para C# e Visual Basic pode ser usado para criar assemblies de arquivo único. Se quiser criar assemblies de vários arquivos, você precisará usar os compiladores de linha de comando ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] para Visual C++.  
  
 Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a>Para criar um assembly com uma extensão .exe  
  
1.  No prompt de comando, digite o seguinte comando:  
  
     \<*comando do compilador*> \<*nome do módulo*>  
  
     Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.  
  
 O exemplo a seguir cria um assembly chamado `myCode.exe` de um módulo de código chamado `myCode`.  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Para criar um assembly com uma extensão .exe e especificar o nome do arquivo de saída  
  
1.  No prompt de comando, digite o seguinte comando:  
  
     \<*comando do compilador*> **/out:**\<*nome de arquivo*> \<*nome do módulo*>  
  
     Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.  
  
 O exemplo a seguir cria um assembly chamado `myAssembly.exe` de um módulo de código chamado `myCode`.  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a>Criando assemblies de biblioteca  
 Um assembly de biblioteca é semelhante a uma biblioteca de classes. Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.  
  
#### <a name="to-create-a-library-assembly"></a>Para criar um assembly de biblioteca  
  
1.  No prompt de comando, digite o seguinte comando:  
  
     \<*comando do compilador*> **/t:library** \<*nome do módulo*>  
  
     Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly. Você também pode usar outras opções do compilador, como a opção **/out:**.  
  
 O exemplo a seguir cria um assembly de biblioteca chamado `myCodeAssembly.dll` de um módulo de código chamado `myCode`.  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)   
 [Assemblies de Vários Arquivos](../../../docs/framework/app-domains/multifile-assemblies.md)   
 [Como compilar um assembly de vários arquivos](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
