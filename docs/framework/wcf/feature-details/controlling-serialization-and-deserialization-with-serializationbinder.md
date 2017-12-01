---
title: "Controlando a serialização e a desserialização sem SerializationBinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be5faf5e465eeacc190081c22d7bc59c3caf5825
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Controlando a serialização e a desserialização sem SerializationBinder
Durante a serialização, um formatador transmite as informações necessárias para criar uma instância de um objeto do tipo correto e a versão. Geralmente, essas informações incluem o nome de tipo completo e o nome de assembly do objeto. Por padrão, a desserialização usa essas informações para criar uma instância de um objeto idêntico. Alguns usuários poderão precisar controlar qual classe para serializar e desserializar, ou porque a classe original pode não existir no computador que está executando a desserialização, a classe original foi movido entre assemblies ou uma versão diferente da classe é necessária do servidor e cliente. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Uso do associador de serialização](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Essa funcionalidade está disponível somente ao usar o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Usando SerializationBinder  
 O <xref:System.Runtime.Serialization.SerializationBinder> é uma classe abstrata usada para controlar os tipos reais usados durante a serialização e a desserialização. Para controlar os tipos usados durante a serialização e desserialização, derive uma classe de <xref:System.Runtime.Serialization.SerializationBinder> e substituir o <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> e <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> métodos. O <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> leva um <xref:System.Type> e retorna um nome de assembly e tipo. O <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> usa um nome de assembly e o tipo de método e retorna um <xref:System.Type>.  
  
## <a name="see-also"></a>Consulte também  
 [Serialização e desserialização](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Uso do associador de serialização](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)
