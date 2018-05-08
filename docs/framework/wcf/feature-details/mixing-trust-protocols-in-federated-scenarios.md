---
title: Misturando protocolos confiáveis em cenários federados
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: bca23ba16c69c6d21ed7cf49aaebb8d2ed079f5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Misturando protocolos confiáveis em cenários federados
Pode haver cenários em que os clientes federados se comunicar com um serviço e um serviço de Token de segurança (STS) que não têm a mesma versão de confiança. O serviço WSDL pode conter um `RequestSecurityTokenTemplate` asserção com elementos de WS-Trust das versões diferentes do que o STS. Nesses casos, um cliente do Windows Communication Foundation (WCF) converte os elementos de WS-Trust recebidos do `RequestSecurityTokenTemplate` para corresponder o STS confiança versão. WCF gerencia versões incompatíveis confiança somente para associações padrão. Todos os parâmetros de algoritmo padrão que são reconhecidos pelo WCF fazem parte da associação padrão. Este tópico descreve o comportamento do WCF com várias configurações de confiança entre o serviço e o STS.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP fevereiro de 2005 e STS fevereiro de 2005  
 O WSDL para terceira parte confiável (RP) contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 O arquivo de configuração do cliente contém uma lista de parâmetros.  
  
 WCF não é possível diferenciar entre os parâmetros de cliente e de serviço; Adiciona todos os parâmetros e as envia no `RequestSecurityTokenTemplate` (primeira).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>RP Trust 1.3 e STS Trust 1.3  
 O WSDL para RP contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 O arquivo de configuração do cliente contém um `secondaryParameters` elemento que encapsula os parâmetros especificados pela RP.  
  
 WCF remove o `EncryptionAlgorithm`, `CanonicalizationAlgorithm` e `KeyWrapAlgorithm` elementos do elemento de nível superior na primeira se estes estiverem dentro do `SecondaryParameters` elemento. WCF anexa o `SecondaryParameters` elemento para a primeira saída sem modificações.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Relação de confiança do RP fevereiro de 2005 e STS Trust 1.3  
 O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 O arquivo de configuração do cliente contém uma lista de parâmetros.  
  
 No arquivo de configuração de cliente WCF não é possível diferenciar entre os parâmetros de cliente e de serviço. Portanto WCF converte todos os parâmetros em um namespace de versão 1.3 de confiança.  
  
 Identificadores WCF a `KeyType`, `KeySize`, e `TokenType` elementos da seguinte maneira:  
  
-   Baixar WSDL, criar a associação e atribuir `KeyType`, `KeySize`, e `TokenType` de parâmetros de RP. O arquivo de configuração do cliente é gerado.  
  
-   O cliente agora pode alterar qualquer parâmetro no arquivo de configuração.  
  
-   Durante a execução, o WCF copia todos os parâmetros especificados para o `AdditionalTokenParameters` seção do arquivo de configuração do cliente, exceto `KeyType`, `KeySize` e `TokenType`, porque esses parâmetros são tratados de durante o arquivo de configuração geração.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>RP Trust 1.3 e a confiança do STS fevereiro de 2005  
 O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 O arquivo de configuração do cliente contém um `secondaryParamters` elemento que encapsula os parâmetros especificados pela RP.  
  
 WCF copia todos os parâmetros especificados dentro de `SecondaryParameters` seção para o elemento de nível superior primeira, mas não convertê-los para o namespace de WS-Trust 2005.
