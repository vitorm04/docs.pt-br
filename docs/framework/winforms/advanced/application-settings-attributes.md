---
title: "Atributos de configurações do aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2ed0a0393f505d0126508e574b1cd9abe138866
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="application-settings-attributes"></a>Atributos de configurações do aplicativo
A arquitetura de Configurações de Aplicativo fornece muitos atributos que podem ser aplicados à classe wrapper de configurações de aplicativos ou suas propriedades individuais. Esses atributos são examinados no tempo de execução pela infraestrutura de configurações de aplicativo, geralmente especificamente pelo provedor de configurações, a fim de adaptar seu funcionamento às necessidades declaradas do wrapper personalizado.  
  
 A tabela a seguir lista os atributos que podem ser aplicados à classe wrapper de configurações de aplicativo, às propriedades individuais desta classe ou a ambos. Por definição, somente um único atributo de escopo —**UserScopedSettingAttribute** ou **ApplicationScopedSettingAttribute**— deve ser aplicado a todas as propriedades de configurações.  
  
> [!NOTE]
>  Um provedor de configurações personalizadas, derivado de <xref:System.Configuration.SettingsProvider> classe, só é necessário para reconhecer os três atributos a seguir: **ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**, e **DefaultSettingValueAttribute**.  
  
|Atributo|Destino|Descrição|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Ambos|Especifica o nome curto do provedor configurações a ser usado para persistência.<br /><br /> Se esse atributo não for fornecido, o provedor padrão, <xref:System.Configuration.LocalFileSettingsProvider>, será assumido.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Ambos|Define uma propriedade como uma configuração de aplicativo no escopo do usuário.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Ambos|Define uma propriedade como uma configuração de aplicativo no escopo do aplicativo.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Propriedade|Especifica uma cadeia de caracteres que pode ser desserializada pelo provedor para o valor padrão embutido em código para essa propriedade.<br /><br /> O <xref:System.Configuration.LocalFileSettingsProvider> não exige esse atributo e substituirá qualquer valor fornecido por este atributo se houver um valor já persistido.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Propriedade|Fornece o teste descritivo para uma configuração individual, usada primariamente por ferramentas de tempo de execução e de tempo de design.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Classe|Fornece um nome explícito para um grupo de configurações. Se esse atributo estiver ausente, <xref:System.Configuration.ApplicationSettingsBase> usa o nome da classe wrapper.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Classe|Fornece o teste descritivo para um grupo de configurações, usado primariamente por ferramentas de tempo de execução e de tempo de design.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Ambos|Especifica zero ou mais serviços de gerenciabilidade que devem ser fornecidos para o grupo de configurações ou propriedade. Os serviços disponíveis são descritos pelo <xref:System.Configuration.SettingsManageability> enumeração.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Propriedade|Indica que uma configuração pertence a uma categoria especial e predefinida, como uma cadeia de conexão, o que sugere um processamento especial pelo provedor de configurações. As categorias predefinidas para este atributo são definidas pelo <xref:System.Configuration.SpecialSetting> enumeração.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Ambos|Especifica um mecanismo preferencial de serialização para um grupo de configurações ou propriedade. Os mecanismos de serialização disponíveis são definidos pelo <xref:System.Configuration.SettingsSerializeAs> enumeração.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Propriedade|Especifica que um provedor de configurações deve desabilitar todas as funcionalidade de atualização de aplicativo para a propriedade marcada.|  
  
 *Classe* indica que o atributo pode ser aplicado somente a uma classe wrapper de configurações de aplicativo. *Propriedade* indica que o atributo pode ser aplicado somente a propriedades de configurações. *Ambos* indica que o atributo pode ser aplicado em qualquer nível.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 [Arquitetura das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [Como criar configurações de aplicativo](http://msdn.microsoft.com/library/53b3af80-1c02-4e35-99c6-787663148945)
