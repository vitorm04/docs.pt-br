---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c0ff11752ae1030e574182cfb825fb87ddc8c7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe XmlDictionaryReaderQuotas não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe XmlDictionaryReaderQuotas tem as seguintes propriedades:  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A extensão máxima permitida da matriz.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O máximo de bytes permitidos retornados para cada leitura.  
  
### <a name="maxdepth"></a>MaxDepth  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 A profundidade máxima do nó aninhado para cada leitura.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O máximo de caracteres permitidos no nome da tabela.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O máximo de caracteres permitidos no conteúdo do elemento XML.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
