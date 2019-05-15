---
title: Nomes de par e IDs de PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: 8cdd5151d029436d11c78806cf7673861cc0d8a4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623115"
---
# <a name="peer-names-and-pnrp-ids"></a>Nomes de par e IDs de PNRP
Um nome de par representa um ponto de extremidade para comunicação, que pode ser um computador, um usuário, um grupo, um serviço ou qualquer elemento associado a um par que pode ser resolvido para um endereço IPv6. O protocolo PNRP usa o nome do par estatisticamente exclusivo para a criação de uma ID de PNRP, que é usado para identificar membros de nuvem.  
  
## <a name="peer-names"></a>Nomes de par  
 Nomes de par podem ser registrados como seguros ou não seguros. Nomes não seguros são apenas cadeias de caracteres de texto que estão sujeitas a falsificação, já que qualquer pessoa pode registrar um nome duplicado não seguro. Nomes não seguros encontram sua melhor aplicação em redes privadas ou protegidas. Nomes seguros são protegidos com um certificado e uma assinatura digital. Somente o editor original poderá comprovar a propriedade de um nome seguro.  
  
 A combinação de nuvem e o escopo fornece um ambiente razoavelmente seguro para pares que participam da atividade PNRP. No entanto, usar um nome de par seguro não garante a segurança geral do aplicativo de rede. A segurança do aplicativo depende de implementação.  
  
 Nomes de par seguros só são registrados pelo seu proprietário e são protegidos com criptografia de chave pública. Um nome de par seguro é considerado pertencente à entidade de par com a chave privada correspondente. A propriedade pode ser comprovada através do endereço de par certificado (CPA), que é assinado usando a chave privada. Um usuário mal-intencionado não pode forjar uma propriedade de um nome de par sem a chave privada correspondente.  
  
## <a name="pnrp-ids"></a>IDs de PNRP  
 ![ID de PNRP](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 IDs de PNRP são compostas do seguinte:  
  
- Os 128 bits superiores, conhecidos como a ID P2P (ponto a ponto), são um hash de um nome de par atribuído ao ponto de extremidade. O nome do par tem o seguinte formato: *Autoridade.Classificador*. Para nomes seguros, *Autoridade* é o hash SHA1 (Secure Hash Algorithm 1) da chave pública do nome de par em caracteres hexadecimais. Para nomes não seguros, a *Autoridade* é o caractere único "0". *Classificador* é uma cadeia de caracteres que identifica o aplicativo. Nenhuma classificação de nome de par pode ser maior que 149 caracteres, incluindo o terminador `null`.  
  
- Os 128 bits inferiores são usados para o Local do Serviço, que é um número gerado que identifica diferentes instâncias da mesma ID P2P na mesma nuvem.  
  
 Essa combinação de ID P2P e Local de Serviço permite que várias IDs de PNRP sejam registradas em um único computador.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
