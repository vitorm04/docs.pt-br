---
title: "-addmodule (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /addmodule
dev_langs:
- CSharp
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 79fdad111b1f059e6a3b00e393ea2474f71db947
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="addmodule-c-compiler-options"></a>/addmodule (opções do compilador C#)
Essa opção adiciona um módulo criado com a opção target:module para a compilação atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a>Arguments  
 `file`, `file2`  
 Um arquivo de saída que contém metadados. O arquivo não pode conter um manifesto do assembly. Para importar mais de um arquivo, separe os nomes de arquivo com vírgula ou ponto e vírgula.  
  
## <a name="remarks"></a>Comentários  
 Todos os módulos adicionados com **/addmodule** devem estar no mesmo diretório que o arquivo de saída em tempo de execução. Ou seja, é possível especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução. Se o módulo não estiver no diretório do aplicativo em tempo de execução, um <xref:System.TypeLoadException> será obtido.  
  
 `file` não pode conter um assembly. Por exemplo, se o arquivo de saída foi criado com [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), seus metadados podem ser importados com **/addmodule**.  
  
 Se o arquivo de saída foi criado com uma opção **/target** diferente de **/target:module**, seus metadados não poderão ser importados com o **/addmodule**, mas poderão ser importados com [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).  
  
 Essa opção do compilador não está disponível no Visual Studio; um projeto não pode referenciar um módulo. Além disso, essa opção do compilador não pode ser alterada programaticamente.  
  
## <a name="example"></a>Exemplo  
 Compile o arquivo de origem `input.cs` e adicione metadados de `metad1.netmodule` e `metad2.netmodule` para produzir `out.exe`:  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)   
 [Assemblies de Vários Arquivos](../../../framework/app-domains/multifile-assemblies.md)   
 [Como Compilar um Assembly de Vários Arquivos](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)

