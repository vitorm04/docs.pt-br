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
ms.openlocfilehash: b5c1178519601d7dcb7c5b3014f413b6436746fb
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816165"
---
# <a name="configuring-cryptography-classes"></a>Configurando classes de criptografia
O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permite que os administradores do computador configurar os algoritmos de criptografia padrão e implementações de algoritmo que usam o .NET Framework e aplicativos escritos corretamente.  Por exemplo, uma empresa que tem sua própria implementação de um algoritmo de criptografia pode fazer essa implementação padrão em vez da implementação é fornecido no SDK do Windows. Embora os aplicativos gerenciados que usam criptografia sempre podem optar por associar explicitamente a uma implementação específica, é recomendável que criar objetos criptográficos usando o sistema de configuração de criptografia.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Mapeando nomes de algoritmo para classes de criptografia](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 Descreve como mapear um nome de algoritmo para uma classe de criptografia.  
  
 [Mapeando identificadores de objeto para algoritmos de criptografia](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 Descreve como mapear um identificador de objeto para um algoritmo de criptografia.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Serviços criptográficos](../../../docs/standard/security/cryptographic-services.md)  
 Fornece uma visão geral dos serviços de criptografia fornecidos pelo SDK do Windows.  
  
 [Esquema de configurações de criptografia](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 Descreve os elementos que mapeiam nomes amigáveis de algoritmo a classes que implementam algoritmos de criptografia.
