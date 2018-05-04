---
title: Configurando classes de criptografia
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b12d5d95a17439308d79d094e8c22206778f3128
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="configuring-cryptography-classes"></a>Configurando classes de criptografia
O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permite que os administradores do computador configurar os algoritmos de criptografia padrão e implementações de algoritmo que usam o .NET Framework e aplicativos escritos corretamente.  Por exemplo, uma empresa que tem sua própria implementação de um algoritmo de criptografia pode fazer essa implementação padrão em vez da implementação fornecida com o [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]. Embora os aplicativos gerenciados que usam criptografia sempre podem optar por associar explicitamente uma implementação específica, é recomendável que criar objetos de criptografia usando o sistema de configuração de criptografia.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeando nomes de algoritmo para classes de criptografia](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Descreve como mapear um nome de algoritmo para uma classe de criptografia.  
  
 [Mapeando identificadores de objeto para algoritmos de criptografia](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Descreve como mapear um identificador de objeto para um algoritmo de criptografia.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)  
 Fornece uma visão geral dos serviços de criptografia fornecidos pelo [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].  
  
 [Esquema de configurações de criptografia](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Descreve os elementos que mapeiam nomes amigáveis de algoritmo a classes que implementam algoritmos de criptografia.
