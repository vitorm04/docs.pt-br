---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 7a5dd305d1cc40e57d0f07f383151dc1a965bdda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513913"
---
# <a name="-verbose"></a>-verbose
Faz com que o compilador a produzir mensagens de status e de erro detalhadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Especificando `-verbose` é o mesmo que especificar `-verbose+`, que faz com que o compilador emita mensagens detalhadas. O padrão para essa opção é `-verbose-`.  
  
## <a name="remarks"></a>Comentários  
 O `-verbose` opção exibe informações sobre o número total de erros emitida pelo compilador, informa quais assemblies são carregados por um módulo e exibe quais arquivos estão sendo compilados no momento.  
  
> [!NOTE]
>  O `-verbose` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e direciona o compilador para exibir informações de status detalhado.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Consulte também
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
