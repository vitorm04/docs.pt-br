---
title: /optionstrict | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
dev_langs:
- VB
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0394d9c1f4c082271316829ef1d226bd97d136c9
ms.lasthandoff: 03/13/2017

---
# <a name="optionstrict"></a>/optionstrict
Impõe semântica de tipo estrito para restringir a conversões de tipo implícito.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. O `/optionstrict+` opção restringe a conversão implícita de tipo. O padrão para essa opção é `/optionstrict-`. O `/optionstrict+` opção é o mesmo que `/optionstrict`. Você pode usar para a semântica de tipo permissivas.  
  
 `custom`  
 Necessário. Avisar quando a semântica de linguagem estrita não for respeitada.  
  
## <a name="remarks"></a>Comentários  
 Quando `/optionstrict+` estiver em efeito, apenas conversões de tipo alargamento podem ser feito implicitamente. Implícita reduzir conversões de tipo, como a atribuição de um `Decimal` tipo de objeto para um objeto de tipo inteiro, são relatados como erros.  
  
 Para gerar avisos de conversões implícitas de tipo restrição, use `/optionstrict:custom`. Use `/nowarn:numberlist` para ignorar os avisos específicos e `/warnaserror:numberlist` para tratar específicos avisos como erros.  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a>Definir /optionstrict no IDE do Visual Studio  
  
1.  Tenha um projeto selecionado no **Solution Explorer**. Sobre o **projeto** menu, clique em **propriedades.** Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique na guia **Compilar**.  
  
3.  Modificar o valor de **Option Strict** caixa.  
  
### <a name="to-set-optionstrict-programmatically"></a>Definir /optionstrict programaticamente  
  
-   Consulte [opção Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `Test.vb` usando a semântica de tipo estrito.  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)   
 [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
