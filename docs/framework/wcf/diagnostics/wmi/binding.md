---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6505fa08ca43e64df224b75500aacbc903783398
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="binding"></a>Associação
WMI de associação  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe de associação não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe de associação tem as seguintes propriedades.  
  
### <a name="bindingelements"></a>Objetos BindingElements  
 Tipo de dados: matriz BindingElement  
  
 Tipo de acesso: somente leitura  
  
 A coleção de elementos implementados pela associação de associação.  
  
### <a name="closetimeout"></a>closeTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo de tempo fornecido para uma operação de fechamento concluir.  
  
### <a name="name"></a>Nome  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O nome da associação.  
  
### <a name="namespace"></a>Namespace  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O namespace XML da associação.  
  
### <a name="opentimeout"></a>openTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo de tempo fornecido para uma operação de abertura concluir.  
  
### <a name="receivetimeout"></a>ReceiveTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo de tempo fornecido para uma operação de recebimento concluir.  
  
### <a name="scheme"></a>Esquema  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 O esquema de transporte URI usado pelas fábricas de canal e ouvinte construídas pela associação.  
  
### <a name="sendtimeout"></a>sendTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo de tempo fornecido para uma operação de envio concluir.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>
