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
ms.openlocfilehash: b9153b4525063d6c52e22d754d68ffa42e914d00
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074895"
---
# <a name="configuring-cryptography-classes"></a>Configurando classes de criptografia
O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permite que os administradores do computador configurar os algoritmos de criptografia padrão e implementações de algoritmo que usam o .NET Framework e aplicativos escritos corretamente.  Por exemplo, uma empresa que tem sua própria implementação de um algoritmo de criptografia pode tornar essa implementação padrão em vez da implementação fornecida no [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)]. Embora os aplicativos gerenciados que usam criptografia sempre podem optar por associar explicitamente a uma implementação específica, é recomendável que criar objetos criptográficos usando o sistema de configuração de criptografia.  
  
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
