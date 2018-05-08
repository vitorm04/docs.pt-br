---
title: -otimizar
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 2f066835c5f864538f281d4c58772e0e60c132f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-optimize"></a>-otimizar
Habilita ou desabilita otimizações do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. O `-optimize-` opção desabilita otimizações do compilador. O `-optimize+` opção habilita as otimizações. Por padrão, as otimizações estão desabilitadas.|  
  
## <a name="remarks"></a>Comentários  
 Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente. No entanto, como a reorganização de código no arquivo de saída, gerar otimizações `-optimize+` pode dificultar a depuração.  
  
 Todos os módulos gerados com `-target:module` para um assembly deve usar o mesmo `-optimize` configurações como o assembly. Para obter mais informações, consulte [-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Você pode combinar o `-optimize` e `-debug` opções.  
  
|Para definir - otimizar no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.<br />     <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modificar o **habilitar otimizações** caixa de seleção.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e habilita otimizações de compilador.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-a depuração (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
