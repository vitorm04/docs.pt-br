---
title: "-nowarn (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowarn
dev_langs:
- CSharp
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: 24
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
ms.openlocfilehash: 3bae7e6d16c044b8f1aeba26de434cdf17479e82
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="nowarn-c-compiler-options"></a>/nowarn (opções do compilador C#)
A opção **/nowarn** permite suprimir a exibição de um ou mais avisos pelo compilador. Separe vários números de aviso com uma vírgula.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Números de aviso que você deseja que o compilador suprima.  
  
## <a name="remarks"></a>Comentários  
 Você só precisa especificar a parte numérica do identificador de aviso. Por exemplo, se quiser suprimir CS0028, você pode especificar `/nowarn:28`.  
  
 O compilador ignorará silenciosamente números de aviso passados para `/nowarn` que eram válidos em versões anteriores, mas que foram removidos do compilador. Por exemplo, CS0679 era válido no compilador no Visual Studio .NET 2002, mas foi removido posteriormente.  
  
 Os avisos a seguir não podem ser suprimidos pela opção `/nowarn`:  
  
-   Aviso do compilador (nível 1) CS2002  
  
-   Aviso do compilador (nível 1) CS2023  
  
-   Aviso do compilador (nível 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto. Para obter detalhes, consulte [Página de Build, Designer de Projeto (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Modifique a propriedade **Suprimir Avisos**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)   
 [Erros do Compilador do C#](../../../csharp/language-reference/compiler-messages/index.md)

