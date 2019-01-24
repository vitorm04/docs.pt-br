---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f24865fb0affa7b4516a14fc05b905995826e82e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597665"
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
