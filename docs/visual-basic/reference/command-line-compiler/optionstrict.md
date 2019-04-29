---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: e18fe451ea4a80ac959ed61b66394920f8bf177f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788928"
---
# <a name="-optionstrict"></a>-optionstrict
Impõe semântica de tipo estrito para restringir conversões de tipo implícito.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. O `-optionstrict+` opção restringe a conversão implícita de tipo. O padrão para essa opção é `-optionstrict-`. O `-optionstrict+` opção é o mesmo que `-optionstrict`. Você pode usar ambos para a semântica de tipo permissível.  
  
 `custom`  
 Necessário. Avise quando a semântica de linguagem estrita não for respeitada.  
  
## <a name="remarks"></a>Comentários  
 Quando `-optionstrict+` é na verdade, apenas conversões de tipo de expansão podem ser feitas implicitamente. Implícita reduzir conversões de tipo, como a atribuição de um `Decimal` tipo de objeto a um objeto de tipo inteiro, são relatados como erros.  
  
 Para gerar avisos para conversões de tipo de estreitamento implícitas, use `-optionstrict:custom`. Use `-nowarn:numberlist` para ignorar os avisos específicos e `-warnaserror:numberlist` para tratar específicos avisos como erros.  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Definir - optionstrict no IDE do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. Sobre o **Project** menu, clique em **propriedades.**   
  
2. Clique na guia **Compilar**.  
  
3. Modificar o valor de **Option Strict** caixa.  
  
### <a name="to-set--optionstrict-programmatically"></a>Definir - optionstrict programaticamente  
  
- Ver [opção Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `Test.vb` usando a semântica de tipo estrito.  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
