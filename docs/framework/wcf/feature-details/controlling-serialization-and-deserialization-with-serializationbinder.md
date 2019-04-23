---
title: Controlando a serialização e a desserialização sem SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: cb2476b55a965e326e492c3c0b77f0be65b2b290
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198524"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Controlando a serialização e a desserialização sem SerializationBinder
Durante a serialização, um formatador transmite as informações necessárias para criar uma instância de um objeto do tipo correto e a versão. Em geral, essas informações incluem o nome completo do tipo e o nome de assembly do objeto. Por padrão, a desserialização usa essas informações para criar uma instância de um objeto idêntico. Alguns usuários talvez seja necessário controlar qual classe serializar e desserializar, seja porque a classe original talvez não exista no computador executando a desserialização, a classe original foi movido entre assemblies ou uma versão diferente da classe é necessária no servidor e cliente. Para obter mais informações, consulte [uso de associador de serialização](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Essa funcionalidade só está disponível ao usar o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou o <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Usando SerializationBinder  
 O <xref:System.Runtime.Serialization.SerializationBinder> é uma classe abstrata usada para controlar os tipos reais usados durante a serialização e a desserialização. Para controlar os tipos usados durante a serialização e desserialização, derive uma classe de <xref:System.Runtime.Serialization.SerializationBinder> e substitua o <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> e <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> métodos. O <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> leva um <xref:System.Type> e retorna um nome de assembly e tipo. O <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> método usa um nome de assembly e tipo e retorna um <xref:System.Type>.  
  
## <a name="see-also"></a>Consulte também

- [Serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Uso do associador de serialização](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
