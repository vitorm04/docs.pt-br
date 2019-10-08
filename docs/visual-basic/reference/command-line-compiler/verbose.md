---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004978"
---
# <a name="-verbose"></a>-verbose
Faz com que o compilador produza mensagens de erro e status detalhados.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>Argumentos  
 `+` &#124; `-`  
 Opcional. Especificar `-verbose` é o mesmo que especificar `-verbose+`, o que faz com que o compilador emita mensagens detalhadas. O padrão para essa opção é `-verbose-`.  
  
## <a name="remarks"></a>Comentários  
 A opção `-verbose` exibe informações sobre o número total de erros emitidos pelo compilador, relata quais assemblies estão sendo carregados por um módulo e exibe quais arquivos estão sendo compilados no momento.  
  
> [!NOTE]
> A opção `-verbose` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e direciona o compilador para exibir informações detalhadas de status.  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
