---
title: "Etapas do processo de serialização"
ms.date: 08/07/2017
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: a4c125493e1b59d329bf4626c45f48b2b222d308
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="steps-in-the-serialization-process"></a>Etapas do processo de serialização
Quando o método <xref:System.Runtime.Serialization.Formatter.Serialize*> é chamado em um [formatador](xref:System.Runtime.Serialization.Formatter), a serialização do objeto procede de acordo com a seguinte sequência de regras:

- Uma verificação é feita para determinar se o formatador tem um seletor substituto. Se tiver, verifique se o seletor substituto administra objetos do tipo determinado. Se o seletor manipular o tipo de objeto, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*?displayProperty=fullName> será chamado no seletor alternativo.

- Se não houver nenhum seletor alternativo ou se ele não manipular o tipo de objeto, uma verificação será feita para determinar se o objeto está marcado com o atributo [Serializable](xref:System.SerializableAttribute). Se o objeto não estiver marcado, uma <xref:System.Runtime.Serialization.SerializationException> será gerada.

- Se o objeto estiver marcado corretamente, verifique se ele implementa a interface <xref:System.Runtime.Serialization.ISerializable>. Se o objeto implementá-la, <xref:System.Runtime.Serialization.ISerializable.GetObjectData*> será chamado no objeto.
  
- Se o objeto não implementar <xref:System.Runtime.Serialization.ISerializable>, a política de serialização padrão será usada, serializando todos os campos não marcados como [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Consulte também  
 [Serialização Binária](binary-serialization.md)   
 [Serialização XML e SOAP](xml-and-soap-serialization.md)
