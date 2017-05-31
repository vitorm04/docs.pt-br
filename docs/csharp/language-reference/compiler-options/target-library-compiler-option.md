---
title: "-target:library (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dll
dev_langs:
- CSharp
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
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
ms.openlocfilehash: f739d778e7bada7f34e42ecfd05364e8cae5d453
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="targetlibrary-c-compiler-options"></a>/target:library (opções do compilador C#)
A opção **/target:library** faz com que o compilador crie uma DLL (biblioteca de vínculo dinâmico) em vez de um arquivo executável (EXE).  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/target:library  
```  
  
## <a name="remarks"></a>Comentários  
 A DLL será criada com a extensão .dll.  
  
 A menos que seja especificado de outra forma com a opção [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usa o nome do primeiro arquivo de entrada.  
  
 Quando especificado na linha de comando, todos os arquivos até a próxima opção **/out** ou **/target:module** são usados para criar o arquivo .dll.  
  
 Ao criar um arquivo .dll, um método [Main](../../../csharp/programming-guide/main-and-command-args/index.md) não é necessário.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades do **Aplicativo**.  
  
3.  Modifique a propriedade **Tipo de saída**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs`, criando `in.dll`:  
  
```console  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [/target (Opções do compilador C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
