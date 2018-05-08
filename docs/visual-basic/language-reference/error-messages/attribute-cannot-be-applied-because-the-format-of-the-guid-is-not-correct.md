---
title: '&#39;&lt;atributo&gt; &#39; não pode ser aplicado porque o formato do GUID &#39; &lt;número&gt; &#39; não está correto'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 93b208b2119942f939a3af223c2f562c6097f7a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;atributo&gt; &#39; não pode ser aplicado porque o formato do GUID &#39; &lt;número&gt; &#39; não está correto
Um `COMClassAttribute` bloco de atributo especifica um identificador globalmente exclusivo (GUID) que não está de acordo com o formato adequado para um GUID. `COMClassAttribute` usa GUIDs para identificar exclusivamente a classe, a interface e o evento de criação.  
  
 Consiste em um GUID de 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários. Ele é gerado por utilitários Microsoft como uuidgen.exe e é garantido como sendo exclusivo no espaço e tempo.  
  
 **ID do erro:** BC32500  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine o GUID correto ou GUIDs necessários para identificar o objeto COM.  
  
2.  Certifique-se de que as cadeias de caracteres GUID apresentadas para o `COMClassAttribute` bloco de atributo foram copiados corretamente.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Guid>  
[Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)

