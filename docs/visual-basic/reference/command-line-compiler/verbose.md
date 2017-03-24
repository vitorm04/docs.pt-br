---
title: /verbose | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f6d8a8b914ccffff72128bbc907482816b95b8a0
ms.lasthandoff: 03/13/2017

---
# <a name="verbose"></a>/verbose
Faz com que o compilador gerar mensagens de status e de erro detalhadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Especificando `/verbose` é o mesmo que especificar `/verbose+`, que faz com que o compilador emita mensagens detalhadas. O padrão para essa opção é `/verbose-`.  
  
## <a name="remarks"></a>Comentários  
 O `/verbose` opção exibe informações sobre o número total de erros emitido pelo compilador, relata que assemblies estão sendo carregados por um módulo e exibe os arquivos que estão sendo compilados no momento.  
  
> [!NOTE]
>  O `/verbose` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e direciona o compilador para exibir informações de status detalhadas.  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
