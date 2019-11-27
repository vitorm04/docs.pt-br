---
title: '#Diretiva ExternalSource'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343826"
---
# <a name="externalsource-directive"></a>Diretiva #ExternalSource

Indica um mapeamento entre linhas específicas de código-fonte e texto externo à origem.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>Partes  

 `StringLiteral`  
 O caminho para a fonte externa.  
  
 `IntLiteral`  
 O número de linha da primeira linha da fonte externa.  
  
 `LogicalLine`  
 A linha em que o erro ocorre na fonte externa.  
  
 `#End ExternalSource`  
 Encerra o bloco de `#ExternalSource`.  
  
## <a name="remarks"></a>Comentários  

 Essa diretiva é usada somente pelo compilador e pelo depurador.  
  
 Um arquivo de origem pode incluir diretivas de origem externas, que indicam um mapeamento entre linhas específicas de código no arquivo de origem e o texto externo à fonte, como um arquivo. aspx. Se forem encontrados erros no código-fonte designado durante a compilação, eles serão identificados como provenientes da fonte externa.  
  
 As diretivas de origem externa não têm nenhum efeito na compilação e não podem ser aninhadas. Eles são destinados ao uso interno somente pelo aplicativo.  
  
## <a name="see-also"></a>Consulte também

- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
