---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: b88cba4d16c5a770a72b47868d11b16cbba6cae8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788954"
---
# <a name="-optioncompare"></a>-optioncompare
Especifica como são feitas comparações de cadeia de caracteres.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode especificar `-optioncompare` em uma das duas formas: `-optioncompare:binary` usar comparações de cadeia de caracteres binária, e `-optioncompare:text` usar comparações de cadeia de caracteres de texto. Por padrão, o compilador usa `-optioncompare:binary`.  
  
 No Microsoft Windows, a página de código atual determina a ordem de classificação binária. Uma ordem de classificação binária típica é da seguinte maneira:  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Comparações de cadeia de caracteres com base em texto são com base em uma ordem de classificação de texto diferencia maiusculas de minúsculas determinada pela localidade do sistema. Uma ordem de classificação de texto típica é da seguinte maneira:  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Definir - optioncompare no IDE do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.   
  
2. Clique na guia **Compilar**.  
  
3. Modificar o valor de **Option Compare** caixa.  
  
### <a name="to-set--optioncompare-programmatically"></a>Definir - optioncompare de maneira programática  
  
- Ver [instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `ProjFile.vb` e usa comparações de cadeia de caracteres binária.  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
