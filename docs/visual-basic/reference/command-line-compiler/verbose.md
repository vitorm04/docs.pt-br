---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f257fce67d8e348b69404411c12ded785cfd68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652123"
---
# <a name="-verbose"></a>-verbose
Faz com que o compilador gerar mensagens de status e de erro detalhadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Especificando `-verbose` é o mesmo que especificar `-verbose+`, que faz com que o compilador emitir mensagens detalhadas. O padrão para essa opção é `-verbose-`.  
  
## <a name="remarks"></a>Comentários  
 O `-verbose` opção exibe informações sobre o número total de erros emitido pelo compilador informa quais assemblies estão sendo carregados por um módulo e exibe os arquivos que são compilados no momento.  
  
> [!NOTE]
>  O `-verbose` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e direciona o compilador para exibir informações de status detalhado.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
