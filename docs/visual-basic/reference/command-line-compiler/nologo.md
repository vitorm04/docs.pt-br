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
Suprime a exibição da faixa de direitos autorais e as mensagens informativas durante a compilação.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-nologo  
```  
  
## <a name="remarks"></a>Comentários  
 Se você especificar `-nologo`, o compilador não exibirá uma faixa de direitos autorais. Por padrão, `-nologo` não está em vigor.  
  
> [!NOTE]
> A opção `-nologo` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e não exibe uma faixa de direitos autorais.  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
