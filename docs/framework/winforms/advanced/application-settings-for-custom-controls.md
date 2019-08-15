---
title: Configurações do aplicativo para controles personalizados
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: a4e477ce1c171b514482623595b2c5565564a2cb
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040466"
---
# <a name="application-settings-for-custom-controls"></a>Configurações do aplicativo para controles personalizados
É necessário concluir algumas tarefas para que os controles personalizados tenham a capacidade de persistir as configurações de aplicativo quando os controles estão hospedados em aplicativos de terceiros.

 A maioria da documentação sobre o recurso de Configurações do Aplicativo é gravada supondo que você está criando um aplicativo autônomo. No entanto, se você estiver criando um controle que outros desenvolvedores hospedarão em seus aplicativos, será necessário executar algumas etapas adicionais para o controle persistir suas configurações corretamente.

## <a name="application-settings-and-custom-controls"></a>Configurações do Aplicativo e Controles Personalizados
 Para que seu controle persista corretamente suas configurações, ele deve encapsular o processo criando sua própria classe de wrapper de configurações de aplicativos dedicados <xref:System.Configuration.ApplicationSettingsBase>, derivada de. Além disso, a classe de controle principal deve <xref:System.Configuration.IPersistComponentSettings>implementar o. A interface contém várias propriedades, bem como dois métodos, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> e <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Se você adicionar seu controle a um formulário usando o **Designer de formulários do Windows** no Visual Studio, Windows Forms será chamado <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automaticamente quando o controle for inicializado; você deve <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> `Dispose` chamar-se no método do seu controle.

 Além disso, é necessário implementar o seguinte na ordem das configurações do aplicativo para que os controles personalizados funcionem corretamente em ambientes de tempo de design como o Visual Studio:

1. Uma classe de configurações de aplicativo personalizada com um construtor que <xref:System.ComponentModel.IComponent> usa um como um único parâmetro. Use essa classe para salvar e carregar todas as configurações do aplicativo. Ao criar uma nova instância dessa classe, passe o controle personalizado usando o construtor.

2. Crie essa classe de configurações personalizadas depois que o controle tiver sido criado e colocado em um formulário, como no manipulador de <xref:System.Windows.Forms.Form.Load> eventos do formulário.

 Para obter instruções sobre como criar uma classe de configurações [personalizadas, consulte Como: Criar configurações](how-to-create-application-settings.md)do aplicativo.

## <a name="settings-keys-and-shared-settings"></a>Chaves de Configurações e Configurações Compartilhadas
 Alguns controles podem ser usados várias vezes dentro do mesmo formulário. Na maioria das vezes, esses controles deverão persistir suas próprias configurações individuais. Com a <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> Propriedade on <xref:System.Configuration.IPersistComponentSettings>, você pode fornecer uma cadeia de caracteres exclusiva que atue para desambiguar várias versões de um controle em um formulário.

 A maneira mais simples de implementar <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> é usar a <xref:System.Windows.Forms.Control.Name%2A> Propriedade do controle para o <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Quando você carrega ou salva as configurações do controle, passa o valor de <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> para para a <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> propriedade da <xref:System.Configuration.ApplicationSettingsBase> classe. As Configurações do Aplicativo usam essa chave exclusiva ao persistir as configurações do usuário para XML. O exemplo de código a seguir mostra a possível aparência da seção `<userSettings>` para uma instância de um controle personalizado chamado `CustomControl1`, que salva uma configuração para sua propriedade `Text`.

```xml
<userSettings>
    <CustomControl1>
        <setting name="Text" serializedAs="string">
            <value>Hello, World</value>
        </setting>
    </CustomControl1>
</userSettings>
```

 Qualquer instância de um controle que não forneça um valor para <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> compartilhará as mesmas configurações.

## <a name="see-also"></a>Consulte também

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Arquitetura das Configurações do Aplicativo](application-settings-architecture.md)
