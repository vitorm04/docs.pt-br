---
title: Controlando a serialização e a desserialização sem SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 29d48560cf25cd5c2e34d7a512d8c7079c65879e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988216"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Controlando a serialização e a desserialização sem SerializationBinder
Durante a serialização, um formatador transmite as informações necessárias para criar uma instância de um objeto do tipo e da versão corretos. Essas informações geralmente incluem o nome completo do tipo e o nome do assembly do objeto. Por padrão, a desserialização usa essas informações para criar uma instância de um objeto idêntico. Alguns usuários podem precisar controlar qual classe serializar e desserializar, porque a classe original pode não existir no computador que executa a desserialização, a classe original foi movida entre assemblies ou uma versão diferente da classe é necessária no servidor e cliente. Para obter mais informações, consulte [uso do associador de serialização](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Essa funcionalidade só está disponível ao usar o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou o <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Usando SerializationBinder  
 O <xref:System.Runtime.Serialization.SerializationBinder> é uma classe abstrata usada para controlar os tipos reais usados durante a serialização e a desserialização. Para controlar os tipos usados durante a serialização e desserialização, derive uma <xref:System.Runtime.Serialization.SerializationBinder> classe de e <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> substitua <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> os métodos e. O <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> método usa um <xref:System.Type> e retorna um assembly e um nome de tipo. O <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> método usa um assembly e um nome de tipo e <xref:System.Type>retorna um.  
  
## <a name="see-also"></a>Consulte também

- [Serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Uso do associador de serialização](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
