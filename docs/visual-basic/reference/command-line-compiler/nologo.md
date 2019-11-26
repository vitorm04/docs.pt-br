---
title: -nologo
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: 03dc98c45a894304a67765c3e49cd19bbb089c8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335428"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
Suppresses display of the copyright banner and informational messages during compilation.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Comentários  
 If you specify `-nologo`, the compiler does not display a copyright banner. By default, `-nologo` is not in effect.  
  
> [!NOTE]
> The `-nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.  
  
## <a name="example"></a>Exemplo  
 The following code compiles `T2.vb` and does not display a copyright banner.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
