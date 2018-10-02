---
title: Misturando protocolos confiáveis em cenários federados
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
ms.openlocfilehash: d4290880d8d708811a95b38356aa61f0d23c89a8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030071"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Misturando protocolos confiáveis em cenários federados
Pode haver situações em que os clientes federados se comunicar com um serviço e um serviço de Token de segurança (STS) que não têm a mesma versão de confiança. O serviço WSDL pode conter um `RequestSecurityTokenTemplate` asserção com elementos de WS-Trust que são de versões diferentes do que o STS. Nesses casos, um cliente do Windows Communication Foundation (WCF) converte os elementos de WS-Trust proveniente do `RequestSecurityTokenTemplate` para coincidir com o STS confiar versão. WCF trata versões incompatíveis confiança apenas para associações padrão. Todos os parâmetros de algoritmo padrão que são reconhecidos por WCF fazem parte da associação padrão. Este tópico descreve o comportamento do WCF com várias configurações de confiança entre o serviço e o STS.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP de fevereiro de 2005 e fevereiro de 2005 do STS  
 O WSDL para terceiros da terceira parte confiável (RP) contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 O arquivo de configuração do cliente contém uma lista de parâmetros.  
  
 O WCF não consegue diferenciar entre os parâmetros de cliente e o serviço; Adiciona todos os parâmetros e as envia no `RequestSecurityTokenTemplate` (RST).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>Relação de confiança RP 1.3 e STS Trust 1.3  
 O WSDL para RP contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 O arquivo de configuração de cliente contém um `secondaryParameters` elemento que encapsula os parâmetros especificados pela RP.  
  
 O WCF remove o `EncryptionAlgorithm`, `CanonicalizationAlgorithm` e `KeyWrapAlgorithm` elementos do elemento de nível superior sob o RST se elas estiverem presentes dentro a `SecondaryParameters` elemento. O WCF anexa o `SecondaryParameters` elemento RST de saída sem modificações.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Relação de confiança RP fevereiro de 2005 e o STS Trust 1.3  
 O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 O arquivo de configuração do cliente contém uma lista de parâmetros.  
  
 Do arquivo de configuração de cliente, o WCF não consegue diferenciar entre os parâmetros de serviço e cliente. Portanto, o WCF converte todos os parâmetros em um namespace de versão 1.3 da relação de confiança.  
  
 Alças do WCF a `KeyType`, `KeySize`, e `TokenType` elementos da seguinte maneira:  
  
-   Baixar WSDL, criar uma associação e atribua `KeyType`, `KeySize`, e `TokenType` dos parâmetros de RP. O arquivo de configuração do cliente é gerado.  
  
-   O cliente agora pode alterar qualquer parâmetro no arquivo de configuração.  
  
-   Durante o tempo de execução, o WCF copia todos os parâmetros especificados para o `AdditionalTokenParameters` seção do arquivo de configuração do cliente, exceto `KeyType`, `KeySize` e `TokenType`, porque esses parâmetros sejam levados em conta durante o arquivo de configuração geração.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>Relação de confiança RP 1.3 e STS Trust fevereiro de 2005  
 O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 O arquivo de configuração de cliente contém um `secondaryParamters` elemento que encapsula os parâmetros especificados pela RP.  
  
 WCF copia todos os parâmetros especificados dentro de `SecondaryParameters` seção ao elemento RST de nível superior, mas não convertê-los para o namespace do WS-Trust de 2005.
