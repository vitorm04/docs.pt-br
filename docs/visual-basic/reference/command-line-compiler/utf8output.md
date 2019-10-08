---
title: -utf8output (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- -utf8output compiler option [Visual Basic]
- utf8output compiler option [Visual Basic]
- /utf8output compiler option [Visual Basic]
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
ms.openlocfilehash: adcb518cbe8397549c3ae3b3a8ca9f0ecf9dc38e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004659"
---
# <a name="-utf8output-visual-basic"></a>-utf8output (Visual Basic)
Exibe a saída do compilador usando a codificação UTF-8.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-utf8output[+ | -]  
```  
  
## <a name="arguments"></a>Argumentos  
 `+` &#124; `-`  
 Opcional. O padrão para essa opção é `-utf8output-`, o que significa que a saída do compilador não usa a codificação UTF-8. Especificar `-utf8output` é o mesmo que especificar `-utf8output+`.  
  
## <a name="remarks"></a>Comentários  
 Em algumas configurações internacionais, a saída do compilador não pode ser exibida corretamente no console do. Nessas situações, use `-utf8output` e redirecione a saída do compilador para um arquivo.  
  
> [!NOTE]
> A opção `-utf8output` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e direciona o compilador para exibir a saída usando a codificação UTF-8.  
  
```console  
vbc -utf8output in.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
