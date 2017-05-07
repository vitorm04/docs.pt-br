---
title: "Seção de configuração do Windows Forms | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
translationtype: Human Translation
ms.sourcegitcommit: 9ff485d8791960f24f727cfc60fbc5ab77203a92
ms.openlocfilehash: fc062bf205db5b2f8883785eb2656eb9d3d8ca16
ms.lasthandoff: 05/02/2017

---
# <a name="windows-forms-configuration-section"></a>Seção de configuração do Windows Forms
As definições de configuração do Windows Forms permitem que um aplicativo do Windows Forms armazene e recupere informações sobre configurações personalizadas de aplicativo, como suporte a vários monitores, suporte ao DPI e outras configurações predefinidas.

As definições de configuração de aplicativo do Windows Forms são armazenadas em um elemento `System.Windows.Forms.ConfigurationSection` do arquivo de configuração de aplicativo.

## <a name="syntax"></a>Sintaxe

```xml
<configuration>
  \<System.Windows.Forms.ConfigurationSection>
  ...
  \</System.Windows.Forms.ConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

nenhuma.

### <a name="child-elements"></a>Elementos filho

Elemento  |Descrição |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | Adiciona uma chave de definição de configuração com um valor especificado |

### <a name="parent-elements"></a>Elementos pai

Elemento  |Descrição |
---------|---------|
[\<configuration>](../configuration-element.md) | O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e Windows Forms |

## <a name="remarks"></a>Comentários

A partir do .NET Framework 4.7, o elemento `<System.Windows.Forms.ConfigurationSection>` permite configurar os aplicativos do Windows Forms para aproveitar os recursos adicionados em versões recentes do .NET Framework. 

O elemento `<System.Windows.Forms.ConfigurationSection>` pode incluir um ou mais elementos [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) filho e cada um deles define uma definição de configuração específica.

## <a name="see-also"></a>Consulte também

[Esquema de arquivo de configuração](../index.md)
[Suporte ao DPI alto no Windows Forms](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)

