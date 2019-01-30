---
title: 'Como: Criar um assembly de arquivo único'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5c0b5dc2e001121ab54447bae4a5eed3290a580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597834"
---
# <a name="how-to-build-a-single-file-assembly"></a>Como: Criar um assembly de arquivo único

Um assembly de arquivo único, que é o tipo mais simples de assembly, contém informações sobre o tipo e a implementação, bem como o [manifesto do assembly](../../../docs/framework/app-domains/assembly-manifest.md). Você pode usar compiladores de linha de comando ou o Visual Studio para criar um assembly de arquivo único. Por padrão, o compilador cria um arquivo do assembly com uma extensão de .exe.

> [!NOTE]
> O Visual Studio para C# e Visual Basic pode ser usado apenas para criar assemblies de arquivo único. Se quiser criar assemblies de vários arquivos, você deverá usar os compiladores de linha de comando ou o Visual C++.

Os procedimentos a seguir mostram como criar assemblies de arquivo único usando compiladores de linha de comando.

## <a name="to-create-an-assembly-with-an-exe-extension"></a>Para criar um assembly com uma extensão .exe

1.  No prompt de comando, digite o seguinte comando:

     \<*comando do compilador*> \<*nome do módulo*>

     Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.

 O exemplo a seguir cria um assembly chamado `myCode.exe` de um módulo de código chamado `myCode`.

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Para criar um assembly com uma extensão .exe e especificar o nome do arquivo de saída

1.  No prompt de comando, digite o seguinte comando:

     \<*comando do compilador*> **/out:**\<*nome de arquivo*> \<*nome do módulo*>

     Neste comando, o *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código, *nome de arquivo* é o nome de arquivo de saída e *nome do módulo* é o nome do módulo do código a ser compilado no assembly.

 O exemplo a seguir cria um assembly chamado `myAssembly.exe` de um módulo de código chamado `myCode`.

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a>Criando assemblies de biblioteca
 Um assembly de biblioteca é semelhante a uma biblioteca de classes. Ele contém tipos que serão referenciados por outros assemblies, mas ele não tem nenhum ponto de entrada para iniciar a execução.

### <a name="to-create-a-library-assembly"></a>Para criar um assembly de biblioteca

1.  No prompt de comando, digite o seguinte comando:

     \<*compiler command*> **-t:library** \<*module name*>

     Neste comando, *comando do compilador* é o comando do compilador para a linguagem usada no módulo do código e *nome do módulo* é o nome do módulo do código a ser compilado no assembly. Você também pode usar outras opções do compilador, como a opção **-out:**.

 O exemplo a seguir cria um assembly de biblioteca chamado `myCodeAssembly.dll` de um módulo de código chamado `myCode`.

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Consulte também

- [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)
- [Assemblies de vários arquivos](../../../docs/framework/app-domains/multifile-assemblies.md)
- [Como: Criar um assembly de vários arquivos](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)