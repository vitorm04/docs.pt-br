---
title: Considerações sobre quando hospedar um controle ActiveX em um Windows Form
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- ActiveX controls [Windows Forms], hosting
- Windows Forms, ActiveX controls
- Windows Forms, hosting ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 2509302d-a74e-484f-9890-2acdbfa67a68
ms.openlocfilehash: 0b95bab20299b966b9f3c6e6ce089a641670f974
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933408"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Considerações sobre quando hospedar um controle ActiveX em um Windows Form
Embora o Windows Forms tenha sido otimizada para hospedar controles dos Windows Forms, você ainda poderá usar controles ActiveX. Lembre-se das seguintes considerações ao planejar um aplicativo que usa os controles ActiveX:  
  
- **Segurança** O Common Language Runtime foi aprimorado em relação à segurança de acesso do código. Aplicativos que contém formulários dos Windows Forms podem ser executados em um ambiente totalmente confiável sem problemas e em um ambiente de confiança parcial com a maioria das funcionalidades acessíveis. Controles dos Windows Forms podem ser hospedados em um navegador sem complicações. No entanto, controles ActiveX nos Windows Forms não podem aproveitar essas melhorias de segurança. A execução de um controle ActiveX requer permissão de código não-gerenciado, que é <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> definida com a propriedade. Para obter mais informações sobre a permissão de segurança e código não- <xref:System.Security.Permissions.SecurityPermissionAttribute>gerenciado, consulte.  
  
- **Custo total de propriedade** Controles ActiveX adicionados a um Windows Form são implantados com esse Windows Form integralmente, o que pode aumentar significativamente o tamanho do arquivo criado. Além disso, usar controles ActiveX nos Windows Forms requer a gravação no Registro. Isso é mais invasivo no computador do usuário que os controles dos Windows Forms, que não exigem isso.  
  
    > [!NOTE]
    > Trabalhar com um controle ActiveX requer o uso de um wrapper de interoperabilidade COM. Para obter mais informações, consulte [Interoperabilidade COM em Visual Basic e Visual C#](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    > Se o nome de um membro do controle ActiveX corresponder a um nome definido no .NET Framework, o importador do controle ActiveX preparará o nome do membro com **CTL** quando ele criar <xref:System.Windows.Forms.AxHost> a classe derivada. Por exemplo, se o controle ActiveX tiver um membro nomeado **layout**, ele será renomeado **CtlLayout** na classe derivada de AxHost porque o evento de **Layout** é definido dentro do .NET Framework.  
  
## <a name="see-also"></a>Consulte também

- [Como: Adicionar controles ActiveX a Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Segurança de acesso do código](../../misc/code-access-security.md)
- [Controles e objetos programáveis comparados em diversas linguagens e bibliotecas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Colocando controles nos Windows Forms](putting-controls-on-windows-forms.md)
- [Controles dos Windows Forms](index.md)
