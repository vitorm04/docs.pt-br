---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: ddb12eb473ce53e60835acb8f1076655f78fafd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574372"
---
# <a name="-optimize"></a>-optimize
Habilita ou desabilita as otimizações do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. O `-optimize-` opção desabilita as otimizações do compilador. O `-optimize+` opção habilita as otimizações. Por padrão, as otimizações estão desabilitadas.|  
  
## <a name="remarks"></a>Comentários  
 Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente. No entanto, porque as otimizações resultam na reorganização de código no arquivo de saída, `-optimize+` pode dificultar a depuração.  
  
 Todos os módulos gerados com `-target:module` para um assembly deve usar a mesma `-optimize` configurações que o assembly. Para obter mais informações, consulte [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Você pode combinar as `-optimize` e `-debug` opções.  
  
|Para definir - otimizar no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.<br />     <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modificar a **habilitar otimizações** caixa de seleção.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e habilita as otimizações do compilador.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Consulte também
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
