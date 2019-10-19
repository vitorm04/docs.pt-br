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
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583082"
---
# <a name="-optionstrict"></a>-optionstrict

Impõe uma semântica de tipo estrito para restringir conversões implícitas de tipo.

## <a name="syntax"></a>Sintaxe

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
Opcional. A opção `-optionstrict+` restringe a conversão de tipo implícita. O padrão para essa opção é `-optionstrict-`. A opção `-optionstrict+` é a mesma que `-optionstrict`. Você pode usar ambas as semânticas de tipo permissivas.

`custom`  
Necessário. Avisar quando a semântica de linguagem estrita não for respeitada.

## <a name="remarks"></a>Comentários

Quando `-optionstrict+` está em vigor, apenas conversões de tipo de alargamento podem ser feitas implicitamente. As conversões de tipo de estreitamento implícita, como a atribuição de um objeto de tipo de `Decimal` a um objeto de tipo inteiro, são relatadas como erros.

Para gerar avisos para conversões de tipo de estreitamento implícita, use `-optionstrict:custom`. Use `-nowarn:numberlist` para ignorar avisos e `-warnaserror:numberlist`s específicos para tratar avisos específicos como erros.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Para Set-optionstrict no IDE do Visual Studio

1. Selecione um projeto no **Gerenciador de Soluções**. No menu **projeto** , clique em **Propriedades.**

2. Clique na guia **Compilar**.

3. Modifique o valor na caixa **Option Strict** .

### <a name="to-set--optionstrict-programmatically"></a>Para Set-optionstrict programaticamente

Consulte a [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Exemplo

O código a seguir compila `Test.vb` usando semântica de tipo estrito.

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
