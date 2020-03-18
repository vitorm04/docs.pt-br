---
title: 'Como: Ver o conteúdo do conjunto'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187381"
---
# <a name="how-to-view-assembly-contents"></a>Como: Ver o conteúdo do conjunto

Você pode usar o [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) para exibir informações MSIL (Microsoft Intermediate Language) em um arquivo. Se o arquivo que está sendo examinado for um conjunto, essas informações podem incluir os atributos e referências da montagem a outros módulos e conjuntos. Essas informações podem ser úteis para determinar se um arquivo é uma montagem ou parte de uma montagem e se o arquivo tem referências a outros módulos ou conjuntos.

Para exibir o conteúdo de um conjunto usando *Ildasm.exe, digite* **o nome de montagem de ildasm \<>** em um prompt de comando. Por exemplo, o comando a seguir desmonta o *conjunto Hello.exe.*

```cmd
ildasm Hello.exe
```

Para visualizar as informações do manifesto de montagem, clique duas vezes no ícone **Manifesto** na janela Desmontador do MSIL.

## <a name="example"></a>Exemplo

O exemplo a seguir começa com um programa básico "Hello World". Depois de compilar o programa, use *Ildasm.exe* para desmontar a montagem *hello.exe* e visualizar o manifesto de montagem.

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

Executar o comando *ildasm.exe* no conjunto *Hello.exe* e clicar duas vezes no ícone **Manifesto** na janela Desmontador do MSIL produz a seguinte saída:

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

A tabela a seguir descreve cada diretiva no manifesto de montagem da assembléia *Hello.exe* usada no exemplo:

|Diretiva|Descrição|
|---------------|-----------------|
|**.assembly extern \<nome de montagem>**|Especifica outro assembly que contém itens referenciados pelo módulo atual (neste exemplo, `mscorlib`).|
|**.publickeytoken \<token>**|Especifica o token da chave real do assembly referenciado.|
|**número \<da versão .ver>**|Especifica o número de versão do assembly referenciado.|
|**.nome \<de montagem>**|Especifica o nome do assembly.|
|**.hash \<algoritmo int32 valor>**|Especifica o algoritmo de hash usado.|
|**número \<da versão .ver>**|Especifica o número de versão do assembly.|
|**.>\<nome do arquivo do módulo**|Especifica o nome dos módulos que compõem o assembly. Neste exemplo, o assembly consiste em apenas um arquivo.|
|**>de \<valor do subsistema**|Especifica o ambiente de aplicativo necessário para o programa. Neste exemplo, o valor 3 indica que este executável é executado em um console.|
|**.corflags**|Atualmente, um campo reservado nos metadados.|

Um manifesto do assembly pode conter várias diretivas diferentes, dependendo do conteúdo do assembly. Para obter uma extensa lista das diretrizes no manifesto de montagem, consulte a documentação do Ecma, especialmente "Partição II: Definição de Metadados e Semântica" e "Partição III: Conjunto de Instruções CIL":

- [Padrões de Infra-estrutura de Linguagem Comum ECMA C# e Common Language](../components.md#applicable-standards)
- [Padrão ECMA-335 - Infra-estrutura de linguagem comum (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>Confira também

- [Domínios e montagens de aplicativos](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Domínios de aplicativos e conjuntos de tópicos de como fazer](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md)
