---
title: Como compilar um assembly de vários arquivos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 916db7ec9bee0c85db1f2fcf4db7a9f8a61f9be3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-build-a-multifile-assembly"></a>Como compilar um assembly de vários arquivos
Este artigo explica como criar um assembly de vários arquivos e fornece código que ilustra cada etapa no procedimento.  
  
> [!NOTE]
>  O IDE do Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único. Se quiser criar assemblies de vários arquivos, você precisará usar os compiladores de linha de comando ou Visual Studio com o Visual C++.  
  
### <a name="to-create-a-multifile-assembly"></a>Para criar um assembly de vários arquivos  
  
1.  Compile todos os arquivos que contêm namespaces referenciados por outros módulos no assembly nos módulos de código. A extensão padrão para módulos de código é .netmodule.  
  
     Por exemplo, digamos que o arquivo `Stringer` tem um namespace chamado `myStringer`, que inclui uma classe chamada `Stringer`. A classe `Stringer` contém um método chamado `StringerMethod` que grava uma única linha no console.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     Use o comando a seguir para compilar esse código:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     Especificar o parâmetro *module* com a opção do compilador **/t:** indica que o arquivo deve ser compilado como um módulo em vez de como um assembly. O compilador produz um módulo chamado `Stringer.netmodule`, que pode ser adicionado a um assembly.  
  
2.  Compile todos os outros módulos, usando as opções do compilador necessárias para indicar os outros módulos que são referenciados no código. Esta etapa usa a opção do compilador **/addmodule**.  
  
     No exemplo a seguir, um módulo de código chamado `Client` tem um método `Main` de ponto de entrada que referencia um método no módulo `Stringer.dll` criado na etapa 1.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     Use o comando a seguir para compilar esse código:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     Especifique a opção **/t:module** porque este módulo será adicionado a um assembly em uma etapa futura. Especifique a opção **/addmodule** porque o código em `Client` referencia um namespace criado pelo código em `Stringer.netmodule`. O compilador produz um módulo chamado `Client.netmodule` que contém uma referência a outro módulo, `Stringer.netmodule`.  
  
    > [!NOTE]
    >  Os compiladores C# e Visual Basic dão suporte à criação de assemblies de vários arquivos diretamente usando as duas sintaxes diferentes a seguir.  
    >   
    >  -   Duas compilações criam um assembly de dois arquivos:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   Uma compilação cria um assembly de dois arquivos:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  Use o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) para criar o arquivo de saída que contém o manifesto do assembly. Esse arquivo contém informações de referência para todos os módulos ou recursos que fazem parte do assembly.  
  
     No prompt de comando, digite o seguinte comando:  
  
     **al** \<*nome do módulo*> \<*nome do módulo*> … **/main:**\<*nome do método*> **/out:**\<*nome de arquivo*> **/target:**\<*tipo de arquivo do assembly*>  
  
     Neste comando, os argumentos *nome do módulo* especificam o nome de cada módulo a ser incluído no assembly. A opção **/main:** especifica o nome do método que é o ponto de entrada do assembly. A opção **/out:** especifica o nome do arquivo de saída, que contém metadados do assembly. A opção **/target:** especifica que o assembly está em um arquivo executável de aplicativo de console (.exe), um arquivo executável do Windows (.win) ou um arquivo de biblioteca (.lib).  
  
     No exemplo a seguir, o Al.exe cria um assembly que é um executável de aplicativo de console chamado `myAssembly.exe`. O aplicativo consiste em dois módulos chamados `Client.netmodule` e `Stringer.netmodule` e o arquivo executável chamado `myAssembly.exe,` que contém apenas metadados do assembly. O ponto de entrada do assembly é o método `Main` na classe `MainClientApp`, que está localizado em `Client.dll`.  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     Você pode usar o [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar o conteúdo de um assembly ou determinar se um arquivo é um assembly ou um módulo.  
  
## <a name="see-also"></a>Consulte também  
 [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)  
 [Como exibir o conteúdo do assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [Como o tempo de execução localiza assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Assemblies de vários arquivos](../../../docs/framework/app-domains/multifile-assemblies.md)
