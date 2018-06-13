---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: e7dbc4d5f06096978c4d93ea20677dcb60bc3fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655919"
---
# <a name="-optioninfer"></a>-optioninfer
Permite o uso de inferência de tipo local nas declarações de variáveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. Especifique `-optioninfer+` para habilitar a inferência de tipo de local ou `-optioninfer-` para bloqueá-la. A opção `-optioninfer`, sem valor especificado, é a mesma de `-optioninfer+`. O valor padrão quando o comutador `-optioninfer` não estiver presente também é `-optioninfer+`. O valor padrão é definido no arquivo de resposta Vbc.rsp.|  
  
> [!NOTE]
>  Você pode usar a opção `-noconfig` para manter os padrões internos do compilador em vez dos especificados no vbc.rsp. O padrão do compilador para essa opção é `-optioninfer-`.  
  
## <a name="remarks"></a>Comentários  
 Se o arquivo de código fonte contém um [opção Infer instrução](../../../visual-basic/language-reference/statements/option-infer-statement.md), a instrução substitui a `-optioninfer` configuração do compilador de linha de comando.  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a>Para definir - optioninfer no IDE do Visual Studio  
  
1.  Selecione um projeto no **Gerenciador de soluções**. No menu **Projeto**, clique em **Propriedades**.  
  
2.  Sobre o **compilar** guia, modifique o valor no **Option infer** caixa.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `test.vb` com a inferência de tipo local habilitada.  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [Página de Compilação, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [Compilando da Linha de Comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
