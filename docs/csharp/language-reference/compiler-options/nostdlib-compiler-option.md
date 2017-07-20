---
title: "-nostdlib (Opções do Compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nostdlib
dev_langs:
- CSharp
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6331adfb0cdd03675af2f147024af8c56e4a3a82
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="nostdlib-c-compiler-options"></a>/nostdlib (opções do compilador C#)
**/nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/nostdlib[+ | -]  
```  
  
## <a name="remarks"></a>Comentários  
 Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.  
  
 Se você não especificar **/nostdlib**, mscorlib.dll será importado para o programa (o mesmo que especificar **/nostdlib-**). Especificar **/nostdlib** é o mesmo que especificar **/nostdlib+**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Clique no botão **Avançado**.  
  
4.  Modifique a propriedade **Não referenciar mscorlib.dll**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
