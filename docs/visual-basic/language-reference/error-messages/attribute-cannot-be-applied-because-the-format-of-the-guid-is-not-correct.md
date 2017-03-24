---
title: "&quot;&lt;atributo&gt;&quot; não pode ser aplicado porque o formato do GUID &quot;&lt;número&gt;&quot; não está correto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32500
- bc32500
dev_langs:
- VB
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f22f9ecd63582e2a346702919cf9154819b8eb0e
ms.lasthandoff: 03/13/2017

---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>'&lt;atributo&gt;' não pode ser aplicado porque o formato do GUID '&lt;número&gt;' não está correto
Um `COMClassAttribute` bloco de atributo especifica um identificador globalmente exclusivo (GUID) que não estão de acordo com o formato adequado para um GUID. `COMClassAttribute`usa GUIDs para identificar exclusivamente a classe, a interface e o evento de criação.  
  
 Um GUID consiste de 16 bytes, dos quais os oito primeiros são numéricos e os oito últimos são binários. Ele é gerado por utilitários Microsoft como uuidgen.exe e é garantido como sendo exclusivo no espaço e tempo.  
  
 **ID do erro:** BC32500  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Determine o GUID correto ou GUIDs necessários para identificar o objeto COM.  
  
2.  Certifique-se de que as cadeias de caracteres GUID apresentadas para o `COMClassAttribute` bloco de atributo são copiados corretamente.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Guid></xref:System.Guid>   
[Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)


