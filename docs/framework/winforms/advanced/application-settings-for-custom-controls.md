---
title: Configurações do aplicativo para controles personalizados
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 69a5caef8bab45503b9f34422de8c2ba2e7f01ff
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317292"
---
# <a name="application-settings-for-custom-controls"></a>Configurações do aplicativo para controles personalizados
É necessário concluir algumas tarefas para que os controles personalizados tenham a capacidade de persistir as configurações de aplicativo quando os controles estão hospedados em aplicativos de terceiros.  
  
 A maioria da documentação sobre o recurso de Configurações do Aplicativo é gravada supondo que você está criando um aplicativo autônomo. No entanto, se você estiver criando um controle que outros desenvolvedores hospedarão em seus aplicativos, será necessário executar algumas etapas adicionais para o controle persistir suas configurações corretamente.  
  
## <a name="application-settings-and-custom-controls"></a>Configurações do Aplicativo e Controles Personalizados  
 Para seu controle persistir suas configurações corretamente, ele deve encapsular o processo criando seus próprios aplicativos dedicados a classe de wrapper de configurações, derivado de <xref:System.Configuration.ApplicationSettingsBase>. Além disso, a classe de controle principal deve implementar o <xref:System.Configuration.IPersistComponentSettings>. A interface contém diversas propriedades, bem como dois métodos, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> e <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Se você adicionar o controle a um formulário usando o **Designer de formulários do Windows** no Visual Studio, Windows Forms chamará <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automaticamente quando o controle é inicializado; é necessário chamar <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> por conta própria no `Dispose` método do seu controle.  
  
 Além disso, é necessário implementar o seguinte na ordem das configurações do aplicativo para que os controles personalizados funcionem corretamente em ambientes de tempo de design como o Visual Studio:  
  
1. Uma classe de configurações de aplicativo personalizado com um construtor que aceita um <xref:System.ComponentModel.IComponent> como um único parâmetro. Use essa classe para salvar e carregar todas as configurações do aplicativo. Ao criar uma nova instância dessa classe, passe o controle personalizado usando o construtor.  
  
2. Crie esta classe de configurações personalizadas depois que o controle foi criado e colocado em um formulário, como o formulário <xref:System.Windows.Forms.Form.Load> manipulador de eventos.  
  
 Para obter instruções sobre como criar uma classe de configurações personalizadas, consulte [como: Criar configurações de aplicativo](how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Chaves de Configurações e Configurações Compartilhadas  
 Alguns controles podem ser usados várias vezes dentro do mesmo formulário. Na maioria das vezes, esses controles deverão persistir suas próprias configurações individuais. Com o <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> propriedade em <xref:System.Configuration.IPersistComponentSettings>, você pode fornecer uma cadeia de caracteres exclusiva que funciona para desambiguar várias versões de um controle em um formulário.  
  
 A maneira mais simples de implementar <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> é usar o <xref:System.Windows.Forms.Control.Name%2A> propriedade do controle para o <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Quando você carregar ou salvar as configurações do controle, você passa o valor de <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> para o <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> propriedade do <xref:System.Configuration.ApplicationSettingsBase> classe. As Configurações do Aplicativo usam essa chave exclusiva ao persistir as configurações do usuário para XML. O exemplo de código a seguir mostra a possível aparência da seção `<userSettings>` para uma instância de um controle personalizado chamado `CustomControl1`, que salva uma configuração para sua propriedade `Text`.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Todas as instâncias de um controle que não fornecer um valor para <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> compartilharão as mesmas configurações.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.IPersistComponentSettings>
- [Arquitetura das configurações do aplicativo](application-settings-architecture.md)
