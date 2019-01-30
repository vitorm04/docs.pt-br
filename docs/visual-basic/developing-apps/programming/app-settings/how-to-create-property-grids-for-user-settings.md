---
title: 'Como: Criar grades de propriedades para configurações de usuário no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Settings object [Visual Basic], creating property grids for user settings
- user settings [Visual Basic], creating property grids
- property grids [Visual Basic], creating for user settings
- property grids
ms.assetid: b0bc737e-50d1-43d1-a6df-268db6e6f91c
ms.openlocfilehash: ac4e1511026047ee70234d638eb8b1689dbd6056
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717851"
---
# <a name="how-to-create-property-grids-for-user-settings-in-visual-basic"></a>Como: Criar grades de propriedades para configurações de usuário no Visual Basic
Você pode criar uma grade de propriedades para configurações de usuário, preenchendo um controle <xref:System.Windows.Forms.PropertyGrid> com as propriedades da configuração de usuário do objeto `My.Settings`.  
  
> [!NOTE]
>  Para que esse exemplo funcione, seu aplicativo deve ter as configurações de usuário definidas. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 O objeto `My.Settings` expõe cada configuração como uma propriedade. O nome da propriedade é o mesmo que o nome da configuração e o tipo de propriedade é o mesmo que o tipo de configuração. O **Escopo** da configuração determina se a propriedade é somente leitura. A propriedade para uma configuração de escopo do **Aplicativo** é somente leitura, enquanto que a propriedade para uma configuração de escopo do **Usuário** é de leitura/gravação. Para obter mais informações, consulte [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
> [!NOTE]
>  Você não pode alterar ou salvar os valores de configurações de escopo do aplicativo em tempo de execução. As configurações de escopo do aplicativo só podem ser alteradas ao criar o aplicativo (por meio do **Designer de Projeto**) ou editando o arquivo de configuração de aplicativo. Para obter mais informações, consulte [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet).  
  
 Este exemplo usa um controle <xref:System.Windows.Forms.PropertyGrid> para acessar as propriedades de configuração do usuário do objeto `My.Settings`. Por padrão, o <xref:System.Windows.Forms.PropertyGrid> mostra todas as propriedades do objeto `My.Settings`. No entanto, as propriedades de configuração do usuário têm um atributo <xref:System.Configuration.UserScopedSettingAttribute>. Este exemplo define a propriedade <xref:System.Windows.Forms.PropertyGrid.BrowsableAttributes%2A> do <xref:System.Windows.Forms.PropertyGrid> como <xref:System.Configuration.UserScopedSettingAttribute> para exibir somente as propriedades de configuração do usuário.  
  
### <a name="to-add-a-user-setting-property-grid"></a>Para adicionar uma grade de propriedades de configuração do usuário  
  
1.  Adicione o controle **PropertyGrid** da **Caixa de Ferramentas** à superfície de design do seu aplicativo, assumido aqui como sendo `Form1`.  
  
     O nome padrão do controle de grade de propriedades é `PropertyGrid1`.  
  
2.  Clique duas vezes na superfície de design para o `Form1` abrir o código para o manipulador de eventos de carregamento de formulário.  
  
3.  Defina o objeto `My.Settings` como o objeto selecionado para a grade de propriedade.  
  
     [!code-vb[VbVbalrMyResources#11](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_1.vb)]  
  
4.  Configure a grade de propriedades para mostrar somente as configurações do usuário.  
  
     [!code-vb[VbVbalrMyResources#12](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-create-property-grids-for-user-settings_2.vb)]  
  
    > [!NOTE]
    >  Para mostrar somente as configurações de escopo do aplicativo, use o atributo <xref:System.Configuration.ApplicationScopedSettingAttribute> em vez de <xref:System.Configuration.UserScopedSettingAttribute>.  
  
## <a name="robust-programming"></a>Programação robusta  
 O aplicativo salva as configurações do usuário quando o aplicativo é desligado. Para salvar as configurações imediatamente, chame o método `My.Settings.Save`. Para obter mais informações, confira [Como: Persistir configurações de usuário em Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md).  
  
## <a name="see-also"></a>Consulte também
- [Objeto My.Settings](../../../../visual-basic/language-reference/objects/my-settings-object.md)
- [Como: ler configurações do aplicativo no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-read-application-settings.md)
- [Como: alterar configurações do usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)
- [Como: persistir configurações de usuário no Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)
- [Gerenciando configurações de aplicativo (.NET)](/visualstudio/ide/managing-application-settings-dotnet)
