---
title: "-unsafe (opções do compilador C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /unsafe
dev_langs:
- CSharp
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.assetid: fdb77ed9-da03-45bd-bb7f-250704da1bcc
caps.latest.revision: 19
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
ms.openlocfilehash: 8f285af57d6a06d38d20b2c28e4a637fbc3ecf2c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="unsafe-c-compiler-options"></a>/unsafe (opções do compilador C#)
A opção do compilador **/unsafe** permite que o código que usa a palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) seja compilado.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/unsafe  
```  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre código não seguro, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Marque a caixa de seleção **Permitir código não seguro**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` para o modo não seguro:  
  
```console  
csc /unsafe in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)

