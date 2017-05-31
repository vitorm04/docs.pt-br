---
title: "-target:winexe (opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /target:winexe
dev_langs:
- CSharp
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: 11
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
ms.openlocfilehash: e9a640c0cfa1d0494457f8ffe94bf15877b24919
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="targetwinexe-c-compiler-options"></a>/target:winexe (opções do compilador C#)
A opção **/target:winexe** faz com que o compilador crie um programa do Windows executável (EXE).  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/target:winexe  
```  
  
## <a name="remarks"></a>Comentários  
 O arquivo executável será criado com a extensão .exe. Um programa do Windows é aquele que fornece uma interface do usuário da biblioteca do .NET Framework ou com as APIs do Win32.  
  
 Use [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) para criar um aplicativo de console.  
  
 A menos que seja especificado de outra forma com a opção [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../../csharp/programming-guide/main-and-command-args/index.md).  
  
 Quando especificado na linha de comando, todos os arquivos até a próxima opção **/out** ou [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) serão usados para criar o programa do Windows.  
  
 Somente um método **Main** é necessário nos arquivos de código-fonte que são compilados em um arquivo .exe. A opção [/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) permite especificar qual classe contém o método **Main**, em casos em que o código tem mais de uma classe com um método **Main**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades do **Aplicativo**.  
  
3.  Modifique a propriedade **Tipo de saída**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` em um programa do Windows:  
  
```console  
csc /target:winexe in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [/target (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
