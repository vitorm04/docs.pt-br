---
title: Esquema de configurações de criptografia
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a7964d01905be4e3dd6e8149e5533e9a2cfd9a71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927627"
---
# <a name="cryptography-settings-schema"></a>Esquema de configurações de criptografia
O esquema de configurações de criptografia contém elementos que especificam como mapear nomes de algoritmo amigáveis para classes que implementam algoritmos de criptografia.  
  
 [ **\<configuration>** ](../configuration-element.md)  
  
 [ **\<mscorlib>** ](mscorlib-element-for-cryptography-settings.md)  
  
 [ **\<cryptographySettings>** ](cryptographysettings-element.md)  
  
 [ **\<cryptoNameMapping>** ](cryptonamemapping-element.md)  
  
 [ **\<cryptoClasses>** ](cryptoclasses-element.md)  
  
 [ **\<cryptoClass>** ](cryptoclass-element.md)  
  
 [ **\<nameEntry>** ](nameentry-element.md)  
  
 [ **\<oidMap>** ](oidmap-element.md)  
  
 [ **\<oidEntry>** ](oidentry-element.md)  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|Contém uma lista de classes de criptografia que têm um mapeamento para um nome amigável no elemento  **\<nameEntry>** .|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|Contém uma classe de criptografia que tem um mapeamento para um nome amigável no elemento **\<nameEntry>** .|  
|[ **\<cryptographySettings**>](cryptographysettings-element.md)|Contém configurações de criptografia.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Contém mapeamentos de classes para nomes amigáveis.|  
|[Elemento **\<mscorlib>** para configurações de criptografia](mscorlib-element-for-cryptography-settings.md)|Contém o elemento **\<cryptographySettings>** .|  
|[ **\<nameEntry>** ](nameentry-element.md)|Mapeia um nome de classe para um nome de algoritmo amigável, o que permite que uma classe tenha vários nomes amigáveis.|  
|[ **\<oidEntry>** ](oidentry-element.md)|Mapeia um OID (identificador de objeto) do ASN.1 para um nome amigável.|  
|[ **\<oidMap>** ](oidmap-element.md)|Contém mapeamentos de OID do ASN.1 para classes.|  
  
## <a name="see-also"></a>Consulte também

- [Esquema de arquivos de configuração](../index.md)
- [Serviços criptográficos](../../../../standard/security/cryptographic-services.md)
