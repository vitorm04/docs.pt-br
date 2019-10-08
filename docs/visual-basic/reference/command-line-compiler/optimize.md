---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005376"
---
# <a name="-optimize"></a>-optimize
Habilita ou desabilita as otimizações do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. A opção `-optimize-` desabilita as otimizações do compilador. A opção `-optimize+` permite otimizações. Por padrão, as otimizações estão desabilitadas.|  
  
## <a name="remarks"></a>Comentários  
 Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente. No entanto, como as otimizações resultam na reorganização de código no arquivo de saída, `-optimize+` pode dificultar a depuração.  
  
 Todos os módulos gerados com `-target:module` para um assembly devem usar as mesmas configurações de `-optimize` que o assembly. Para obter mais informações, consulte [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Você pode combinar as opções `-optimize` e `-debug`.  
  
|Para definir-otimizar no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.<br />     <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modifique a caixa de seleção **habilitar otimizações** .|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e habilita as otimizações do compilador.  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
