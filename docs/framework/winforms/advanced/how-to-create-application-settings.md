---
title: Como criar configurações de aplicativo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
ms.openlocfilehash: 7a84fc85b42f2b78ccafcae3c815847633b9916d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47069982"
---
# <a name="how-to-create-application-settings"></a>Como criar configurações de aplicativo
Usando código gerenciado, é possível criar novas configurações de aplicativo e associá-las a propriedades no seu formulário ou aos controles de formulário, para que essas configurações sejam carregadas e salvas automaticamente no tempo de execução.  
  
 No procedimento a seguir, você criar manualmente uma classe wrapper que deriva de <xref:System.Configuration.ApplicationSettingsBase>. Uma propriedade publicamente acessível é adicionada a essa classe para cada configuração de aplicativo que você desejar expor.  
  
 Também é possível executar esse procedimento usando o mínimo de código possível no designer do Visual Studio.  Consulte também [Como criar configurações de aplicativo usando o Designer](https://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).  
  
### <a name="to-create-new-application-settings-programmatically"></a>Criar novas configurações de aplicativo com programação  
  
1.  Adicione uma nova classe ao seu projeto e renomeie-o. Para este procedimento, chamaremos essa classe de `MyUserSettings`. Altere a definição de classe para que a classe deriva de <xref:System.Configuration.ApplicationSettingsBase>.  
  
2.  Definir uma propriedade nesta classe wrapper para cada configuração de aplicativo precisar e aplique essa propriedade ou com o <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>, dependendo do escopo da configuração. Para obter mais informações sobre o escopo das configurações, consulte [Visão geral de configurações de aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md). Agora, seu código deverá se parecer com o seguinte:  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  Crie uma instância dessa classe wrapper no seu aplicativo. Ela geralmente será um membro privado do formulário principal. Agora que você definiu sua classe, você precisa vinculá-la a uma propriedade; Nesse caso, o <xref:System.Windows.Forms.Form.BackColor%2A> propriedade do seu formulário. Você pode fazer isso no manipulador de eventos `Load` do seu formulário.  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  Se você fornecer uma maneira de alterar as configurações no tempo de execução, será necessário salvar as configurações atuais do usuário no disco quando o formulário for fechado, caso contrário, essas alterações serão perdidas.  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     Agora você criou com êxito uma nova configuração de aplicativo e a associou à propriedade especificada.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 O provedor de configurações padrão, <xref:System.Configuration.LocalFileSettingsProvider>, persiste informações para os arquivos de configuração como texto sem formatação. Isso limita a segurança à segurança de acesso aos arquivos fornecida pelo sistema operacional para o usuário atual. Por isso, é necessário ter cuidado com as informações armazenadas nos arquivos de configuração. Por exemplo, um uso comum para configurações de aplicativo é armazenar cadeias de conexão que apontam para o armazenamento de dados do aplicativo. No entanto, devido a questões de segurança, tais cadeias de caracteres não devem incluir senhas. Para obter mais informações sobre cadeias de caracteres de conexão, consulte <xref:System.Configuration.SpecialSetting>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Visão Geral das Configurações do Aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Como validar configurações de aplicativo](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
