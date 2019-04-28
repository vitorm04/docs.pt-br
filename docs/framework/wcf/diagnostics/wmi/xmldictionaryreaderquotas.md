---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f1c12a0a60397a84d4e9ff0241c4182b4511af5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858423"
---
# <a name="xmldictionaryreaderquotas"></a>XmlDictionaryReaderQuotas
XmlDictionaryReaderQuotas  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
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
 A classe XmlDictionaryReaderQuotas não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe XmlDictionaryReaderQuotas tem as seguintes propriedades:  
  
### <a name="maxarraylength"></a>MaxArrayLength  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 A extensão máxima permitida da matriz.  
  
### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O máximo de bytes permitidos retornados para cada leitura.  
  
### <a name="maxdepth"></a>MaxDepth  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 A profundidade máxima do nó aninhado para cada leitura.  
  
### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O máximo de caracteres permitidos no nome da tabela.  
  
### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O máximo de caracteres permitidos no conteúdo do elemento XML.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
