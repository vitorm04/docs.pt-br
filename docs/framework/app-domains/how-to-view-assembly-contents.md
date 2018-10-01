---
title: Como exibir o conteúdo de um assembly
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abe4c130fb5da49ed0f53c776e23dba8fb5b15f7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47157045"
---
# <a name="how-to-view-assembly-contents"></a>Como exibir o conteúdo de um assembly
Você pode usar o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para exibir informações MSIL (Microsoft Intermediate Language) em um arquivo. Se o arquivo que estiver sendo examinado for um assembly, essas informações poderão incluir os atributos do assembly, bem como as referências a outros módulos e assemblies. Essas informações podem ser úteis para determinar se um arquivo é um assembly ou parte de um assembly e se o arquivo possui referências a outros módulos ou assemblies.  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a>Para exibir o conteúdo de um assembly usando Ildasm.exe  
  
1.  Digite **ildasm** \<*nome do assembly*> no prompt de comando. Por exemplo, o comando a seguir desmonta o assembly `Hello.exe`.  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a>Para exibir informações do manifesto do assembly  
  
1.  Clique duas vezes no ícone MANIFESTO da janela Desmontador de MSIL.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inicia com um programa básico "Hello, World". Após a compilação do programa, use Ildasm.exe para desmontar o assembly Hello.exe e exibir o manifesto do assembly.  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 Executar o comando ildasm.exe no assembly Hello.exe e clicar duas vezes no ícone MANIFESTO da janela IL DASM gera o seguinte resultado:  
  
```  
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
  
 A tabela a seguir descreve cada diretiva no manifesto do assembly de Hello.exe usado no exemplo.  
  
|Diretiva|Descrição|  
|---------------|-----------------|  
|**.assembly extern \<** *nome do assembly* **>**|Especifica outro assembly que contém itens referenciados pelo módulo atual (neste exemplo, `mscorlib`).|  
|**.publickeytoken \<** *token* **>**|Especifica o token da chave real do assembly referenciado.|  
|**.ver \<** *número da versão* **>**|Especifica o número de versão do assembly referenciado.|  
|**.assembly \<** *nome do assembly* **>**|Especifica o nome do assembly.|  
|**.hash algorithm \<** *valor int32* **>**|Especifica o algoritmo de hash usado.|  
|**.ver \<** *número da versão* **>**|Especifica o número de versão do assembly.|  
|**.module \<** *nome de arquivo* **>**|Especifica o nome dos módulos que compõem o assembly. Neste exemplo, o assembly consiste em apenas um arquivo.|  
|**.subsystem \<** *valor* **>**|Especifica o ambiente de aplicativo necessário para o programa. Neste exemplo, o valor 3 indica que este executável é executado em um console.|  
|**.corflags**|Atualmente, um campo reservado nos metadados.|  
  
 Um manifesto do assembly pode conter várias diretivas diferentes, dependendo do conteúdo do assembly. Para obter uma lista extensa das diretivas no manifesto do assembly, confira a documentação da ECMA, especialmente "Partition II: Metadata Definition and Semantics" e "Partition III: CIL Instruction Set". A documentação está disponível online; confira [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212), no MSDN, e [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552), no site internacional da Ecma.  
  
## <a name="see-also"></a>Consulte também  
 [Domínios do aplicativo e assemblies](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [Tópicos explicativos sobre domínios do aplicativo e assemblies](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
