---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: 75369c3bcb19afbf98bfb80bc3e439f996d2a9d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796072"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
Exibe a saída do compilador usando a codificação UTF-8.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. O padrão para essa opção é `-utf8output-`, que significa que a saída do compilador não usa a codificação UTF-8. Especificando `-utf8output` é o mesmo que especificar `-utf8output+`.  
  
## <a name="remarks"></a>Comentários  
 Em algumas configurações internacionais, saída do compilador não pode ser exibida corretamente no console. Em tais situações, use `-utf8output` e redirecione a saída do compilador para um arquivo.  
  
> [!NOTE]
>  O `-utf8output` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e direciona o compilador para exibir saída usando a codificação UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
