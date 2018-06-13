---
title: Configurações do aplicativo para controles personalizados
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], application settings
- application settings [Windows Forms], custom controls
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
ms.openlocfilehash: 46300f679471874ac5046d0a1077d8abca57f2c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518558"
---
# <a name="application-settings-for-custom-controls"></a>Configurações do aplicativo para controles personalizados
É necessário concluir algumas tarefas para que os controles personalizados tenham a capacidade de persistir as configurações de aplicativo quando os controles estão hospedados em aplicativos de terceiros.  
  
 A maioria da documentação sobre o recurso de Configurações do Aplicativo é gravada supondo que você está criando um aplicativo autônomo. No entanto, se você estiver criando um controle que outros desenvolvedores hospedarão em seus aplicativos, será necessário executar algumas etapas adicionais para o controle persistir suas configurações corretamente.  
  
## <a name="application-settings-and-custom-controls"></a>Configurações do Aplicativo e Controles Personalizados  
 Para seu controle persistir suas configurações corretamente, ele deve encapsular o processo criando suas própria aplicativos dedicados a classe de wrapper de configurações, derivado de <xref:System.Configuration.ApplicationSettingsBase>. Além disso, a classe de controle principal deve implementar o <xref:System.Configuration.IPersistComponentSettings>. A interface contém várias propriedades, bem como dois métodos, <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> e <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>. Se você adicionar o controle a um formulário usando o **Windows Forms Designer** no Visual Studio, o Windows Forms chamará <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> automaticamente quando o controle é inicializado; você deve chamar <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> você mesmo o `Dispose` método de seu controle.  
  
 Além disso, é necessário implementar o seguinte na ordem das configurações do aplicativo para que os controles personalizados funcionem corretamente em ambientes de tempo de design como o Visual Studio:  
  
1.  Uma classe de configurações de aplicativo personalizado com um construtor que aceita um <xref:System.ComponentModel.IComponent> como um único parâmetro. Use essa classe para salvar e carregar todas as configurações do aplicativo. Ao criar uma nova instância dessa classe, passe o controle personalizado usando o construtor.  
  
2.  Crie esta classe de configurações personalizadas depois que o controle foi criado e colocado em um formulário, como o formulário <xref:System.Windows.Forms.Form.Load> manipulador de eventos.  
  
 Para obter instruções sobre como criar uma classe de configurações personalizadas, consulte [Como Criar Configurações de Aplicativo](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
## <a name="settings-keys-and-shared-settings"></a>Chaves de Configurações e Configurações Compartilhadas  
 Alguns controles podem ser usados várias vezes dentro do mesmo formulário. Na maioria das vezes, esses controles deverão persistir suas próprias configurações individuais. Com o <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> propriedade <xref:System.Configuration.IPersistComponentSettings>, você pode fornecer uma cadeia de caracteres exclusiva que funciona para desambiguar várias versões de um controle em um formulário.  
  
 A maneira mais simples de implementar <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> é usar o <xref:System.Windows.Forms.Control.Name%2A> propriedade do controle para o <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A>. Quando você carregar ou salva as configurações do controle, você passa o valor de <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> para o <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> propriedade o <xref:System.Configuration.ApplicationSettingsBase> classe. As Configurações do Aplicativo usam essa chave exclusiva ao persistir as configurações do usuário para XML. O exemplo de código a seguir mostra a possível aparência da seção `<userSettings>` para uma instância de um controle personalizado chamado `CustomControl1`, que salva uma configuração para sua propriedade `Text`.  
  
```xml  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 Todas as instâncias de um controle que não forneça um valor para <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> compartilha as mesmas configurações.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.IPersistComponentSettings>  
 [Arquitetura das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)
