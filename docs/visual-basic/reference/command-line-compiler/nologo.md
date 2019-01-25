---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 1b9cedc3e45795a66c203d4c86bb071045a1d3f5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550468"
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
