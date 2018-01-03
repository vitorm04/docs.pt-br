---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e157fb0e1fcdb3899440eed02a42b16f75541989
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="optimize"></a>/optimize
Habilita ou desabilita otimizações do compilador.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. O `/optimize-` opção desabilita otimizações do compilador. O `/optimize+` opção habilita as otimizações. Por padrão, as otimizações estão desabilitadas.|  
  
## <a name="remarks"></a>Comentários  
 Otimizações do compilador tornam o arquivo de saída menor, mais rápido e mais eficiente. No entanto, como a reorganização de código no arquivo de saída, gerar otimizações `/optimize+` pode dificultar a depuração.  
  
 Todos os módulos gerados com `/target:module` para um assembly deve usar o mesmo `/optimize` configurações como o assembly. Para obter mais informações, consulte [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).  
  
 Você pode combinar o `/optimize` e `/debug` opções.  
  
|Para definir /Optimize no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.<br />     <br />2.  Clique na guia **Compilar**.<br />3.  Clique no botão **Avançado**.<br />4.  Modificar o **habilitar otimizações** caixa de seleção.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e habilita otimizações de compilador.  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
