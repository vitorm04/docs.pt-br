---
title: "-target:exe (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /exe
dev_langs:
- CSharp
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 12
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9d5784186f564241c896333d518e297c3c094f28
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="targetexe-c-compiler-options"></a>/target:exe (opções do compilador C#)
A opção **/target:exe** faz com que o compilador crie um aplicativo de console executável (EXE).  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/target:exe  
```  
  
## <a name="remarks"></a>Comentários  
 A opção **/target:exe** está em vigor por padrão. O arquivo executável será criado com a extensão .exe.  
  
 Use [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) para criar um executável de programa do Windows.  
  
 A menos que seja especificado de outra forma com a opção [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../../csharp/programming-guide/main-and-command-args/index.md).  
  
 Quando especificado na linha de comando, todos os arquivos até a próxima opção **/out** ou **/target:module** serão usados para criar o arquivo .exe  
  
 Somente um método **Main** é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. A opção do compilador [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) permite especificar qual classe contém o método **Main**, em casos em que o código tem mais de uma classe com um método **Main**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades do **Aplicativo**.  
  
3.  Modifique a propriedade **Tipo de saída**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Cada uma das seguintes linhas de comando compilará `in.cs`, criando `in.exe`:  
  
```console  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [/target (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
