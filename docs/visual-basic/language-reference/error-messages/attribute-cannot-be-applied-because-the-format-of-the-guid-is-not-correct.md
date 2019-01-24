---
title: '&#39;&lt;atributo&gt; &#39; não pode ser aplicado porque o formato do GUID &#39; &lt;número&gt; &#39; não está correto'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 85b8c9dcccbb307d8a744e33a5f1d4b1775fda04
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623658"
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;atributo&gt; &#39; não pode ser aplicado porque o formato do GUID &#39; &lt;número&gt; &#39; não está correto
Um `COMClassAttribute` bloco de atributo especifica um identificador global exclusivo (GUID) que não corresponde ao formato adequado para um GUID. `COMClassAttribute` usa GUIDs para identificar exclusivamente a classe, a interface e o evento de criação.  
  
 Um GUID consiste em 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários. Ele é gerado pelo utilitários da Microsoft, como uuidgen.exe e é garantido que seja exclusivo no espaço e tempo.  
  
 **ID do erro:** BC32500  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine o GUID correto ou GUIDs necessários para identificar o objeto COM.  
  
2.  Certifique-se de que as cadeias de caracteres GUID apresentadas para o `COMClassAttribute` bloco de atributo são copiados corretamente.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Guid>
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

