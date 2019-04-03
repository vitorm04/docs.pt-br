---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822551"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Suprime a exibição da faixa de direitos autorais e mensagens informativas durante a compilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Comentários  
 Se você especificar `-nologo`, o compilador não exibirá uma faixa de direitos autorais. Por padrão, `-nologo` não está em vigor.  
  
> [!NOTE]
>  O `-nologo` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e não exibirá uma faixa de direitos autorais.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
