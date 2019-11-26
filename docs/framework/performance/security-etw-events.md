---
title: Eventos ETW de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974872"
---
# <a name="security-etw-events"></a>Eventos ETW de segurança

Os eventos de segurança são gerados durante a verificação de nome forte e a verificação de Authenticode.  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>Eventos StrongNameVerificationStart_V1 e StrongNameVerificationStop_V1  
 A tabela a seguir mostra a palavra-chave e o nível. (Para obter mais informações, consulte [Palavras-chaves e níveis CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`SecurityKeyword`(0x400)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Início da verificação de nome forte.|  
|`StrongNameVerificationStop_V1`|182|Fim da verificação de nome forte.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Os sinalizadores de verificação.|  
|ErrorCode|win:UInt32|O código de erro HResult.|  
|FullyQualifiedAssemblyName|win:UnicodeString|O nome totalmente qualificado do assembly.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>Eventos AuthenticodeVerificationStart_V1 e AuthenticodeVerificationStop_V1  
 A tabela a seguir mostra a palavra-chave e o nível.  
  
|Palavra-chave para acionar o evento|Nível|  
|-----------------------------------|-----------|  
|`SecurityKeyword`(0x400)|Informativo(4)|  
  
 A tabela a seguir mostra as informações do evento.  
  
|evento|ID do evento|Acionado quando|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Início da verificação de Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Fim da verificação de Authenticode.|  
  
 A tabela a seguir mostra os dados do evento.  
  
|Nome do campo|Tipo de dados|Descrição|  
|----------------|---------------|-----------------|  
|VerificationFlags|win:UInt32|Os sinalizadores de verificação.|  
|ErrorCode|win:UInt32|O código de erro HResult.|  
|ModulePath|win:UnicodeString|O caminho do módulo.|  
|ClrInstanceID|win:UInt16|ID exclusiva da instância do CLR ou do CoreCLR.|  
  
## <a name="see-also"></a>Consulte também

- [Eventos de CLR ETW](clr-etw-events.md)
