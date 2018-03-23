---
title: -optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2ff7d13fcb3e224ee76cdb42f3974a4eddb042f5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-optionstrict"></a>-optionstrict
Impõe a semântica de tipo estrito para restringir a conversões de tipo implícito.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. O `-optionstrict+` opção restringe a conversão implícita de tipo. O padrão para essa opção é `-optionstrict-`. O `-optionstrict+` opção é o mesmo que `-optionstrict`. Você pode usar para a semântica de tipo permissivo.  
  
 `custom`  
 Necessário. Avise quando a semântica de linguagem estrita não for respeitada.  
  
## <a name="remarks"></a>Comentários  
 Quando `-optionstrict+` está em vigor, conversões de tipo de expansão somente pode ser feito implicitamente. Implícita de conversões de tipo, como a atribuição entre um `Decimal` tipo de objeto para um objeto de tipo inteiro, são relatados como erros.  
  
 Para gerar avisos para conversões de tipo de restrição implícita, use `-optionstrict:custom`. Use `-nowarn:numberlist` para ignorar os avisos específicos e `-warnaserror:numberlist` para tratar específicos avisos como erros.  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Para definir - optionstrict no IDE do Visual Studio  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. Sobre o **projeto** menu, clique em **propriedades.**   
  
2.  Clique na guia **Compilar**.  
  
3.  Modificar o valor de **Option Strict** caixa.  
  
### <a name="to-set--optionstrict-programmatically"></a>Definir - optionstrict programaticamente  
  
-   Consulte [opção Strict instrução](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `Test.vb` usando semântica de tipo estrito.  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [-/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
