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
ms.openlocfilehash: babae31a3be9775d07ca84c54e1177d297cab5cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108752"
---
# <a name="considerations-when-hosting-an-activex-control-on-a-windows-form"></a>Considerações sobre quando hospedar um controle ActiveX em um Windows Form
Embora o Windows Forms tenha sido otimizada para hospedar controles dos Windows Forms, você ainda poderá usar controles ActiveX. Lembre-se das seguintes considerações ao planejar um aplicativo que usa os controles ActiveX:  
  
-   **Segurança** O Common Language Runtime foi aprimorado em relação à segurança de acesso do código. Aplicativos que contém formulários dos Windows Forms podem ser executados em um ambiente totalmente confiável sem problemas e em um ambiente de confiança parcial com a maioria das funcionalidades acessíveis. Controles dos Windows Forms podem ser hospedados em um navegador sem complicações. No entanto, controles ActiveX nos Windows Forms não podem aproveitar essas melhorias de segurança. A execução de um controle ActiveX requer permissão de código não gerenciado, que é definido com o <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A?displayProperty=nameWithType> propriedade. Para obter mais informações sobre segurança e a permissão de código não gerenciado, consulte <xref:System.Security.Permissions.SecurityPermissionAttribute>.  
  
-   **Custo total de propriedade** Controles ActiveX adicionados a um Windows Form são implantados com esse Windows Form integralmente, o que pode aumentar significativamente o tamanho do arquivo criado. Além disso, usar controles ActiveX nos Windows Forms requer a gravação no Registro. Isso é mais invasivo no computador do usuário que os controles dos Windows Forms, que não exigem isso.  
  
    > [!NOTE]
    >  Trabalhar com um controle ActiveX requer o uso de um wrapper de interoperabilidade COM. Para obter mais informações, consulte [Interoperabilidade COM em Visual Basic e Visual C#](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
    > [!NOTE]
    >  Se o nome de um membro do controle ActiveX corresponder a um nome definido na [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], em seguida, o importador de controle ActiveX prefixará o nome do membro com **Ctl** quando ele cria o <xref:System.Windows.Forms.AxHost> classe derivada. Por exemplo, se o controle ActiveX tiver um membro chamado **Layout**, ele será renomeado para **CtlLayout** na classe derivada de AxHost, pois o evento **Layout** é definido dentro do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Consulte também

- [Como: Adicionar controles ActiveX ao Windows Forms](how-to-add-activex-controls-to-windows-forms.md)
- [Segurança de acesso do código](../../misc/code-access-security.md)
- [Controles e objetos programáveis comparados em diversas linguagens e bibliotecas](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Colocando controles nos Windows Forms](putting-controls-on-windows-forms.md)
- [Controles dos Windows Forms](index.md)
