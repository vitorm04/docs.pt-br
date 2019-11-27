---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 72a5638a5c5364381ffd68604b0d44830d53f365
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344208"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Faz com que o compilador aceite apenas a sintaxe que está incluída na versão especificada do idioma de Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>Argumentos  
 `version`  
 Necessária. A versão de idioma a ser usada durante a compilação. Os valores aceitos são `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` e `latest`.

 Qualquer um dos números inteiros também pode ser especificado usando `.0` como a versão secundária, por exemplo, `11.0`.

 Você pode ver a lista de todos os valores possíveis especificando `-langversion:?` na linha de comando.  
  
## <a name="remarks"></a>Comentários  
 A opção `-langversion` especifica a sintaxe aceita pelo compilador. Por exemplo, se você especificar que a versão do idioma é 9,0, o compilador gerará erros de sintaxe válida somente na versão 10,0 e posterior.  
  
 Você pode usar essa opção ao desenvolver aplicativos direcionados a diferentes versões do .NET Framework. Por exemplo, se você estiver direcionando .NET Framework 3,5, poderá usar essa opção para garantir que não use a sintaxe da versão de linguagem 10,0.  
  
 Você pode definir `-langversion` diretamente usando a linha de comando. Para obter mais informações, consulte [Definindo uma versão específica do .NET Framework como destino](/visualstudio/ide/visual-studio-multi-targeting-overview).  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `sample.vb` para Visual Basic 9,0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Direcionamento de uma versão específica do .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview)
