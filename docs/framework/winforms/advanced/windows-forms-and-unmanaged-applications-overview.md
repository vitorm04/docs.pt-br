---
title: Visão geral sobre aplicativos do Windows Forms e aplicativos não gerenciados
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop
- ActiveX controls [Windows Forms], about ActiveX controls
- Windows Forms, interop
ms.assetid: 0a26d99d-8135-4895-8760-c9a2b5f67f14
ms.openlocfilehash: b2ea15703b09cd722f5c7fd01f8112482f3c04f2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488190"
---
# <a name="windows-forms-and-unmanaged-applications-overview"></a>Visão geral sobre aplicativos do Windows Forms e aplicativos não gerenciados
Aplicativos do Windows Forms e controles podem interoperar com aplicativos não gerenciados, com algumas restrições. As seções a seguir descrevem os cenários e as configurações com suporte em controles e aplicativos do Windows Forms e aqueles que não têm suporte.  
  
## <a name="windows-forms-controls-and-activex-applications"></a>Aplicativos ActiveX e controles do Windows Forms  
 Com exceção do Microsoft Internet Explorer e MFC (Microsoft Foundation Classes), não há suporte aos controles do Windows Forms em aplicativos projetados para hospedar controles ActiveX. Outros aplicativos e ferramentas de desenvolvimento que são capazes de hospedar controles ActiveX, inclusive os contêineres de teste ActiveX de versões do Visual Studio anteriores ao Visual Studio .NET 2003, não são hosts com suporte para controles do Windows Forms.  
  
 Essas restrições também se aplicam ao uso de controles do Windows Forms por meio da interoperabilidade COM (Component Object Model). Há suporte para o uso de um controle do Windows Forms por meio de um CCW de COM (COM callable wrapper) somente no Internet Explorer. Para obter mais informações sobre a interoperabilidade COM, consulte  
  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md).  
  
 A tabela a seguir mostra o suporte para hospedagem do ActiveX para controles do Windows Forms.  
  
|Versão do Windows Forms|Suporte|  
|---------------------------|-------------|  
|.NET Framework versão 1.0|Internet Explorer 5.01 e versões posteriores|  
|.NET framework versão 1.1 e posterior|Internet Explorer 5.01 e versões posteriores<br /><br /> MFC (Microsoft Foundation Classes) 7.0 e posterior|  
  
## <a name="hosting-windows-forms-components-as-activex-controls"></a>Hospedando componentes do Windows Forms como controles ActiveX  
 No .NET Framework 1.1, o suporte foi estendido para incluir MFC 7.0 e versões posteriores. Esse suporte inclui qualquer contêiner totalmente compatível com contêiner de controle ActiveX do MFC 7.0 e posterior.  
  
 No entanto, não há suporte para registro dos controles do Windows Forms como controles ActiveX. Além disso, não há suporte chamar o método `com.ms.win32.Ole32.CoCreateInstance` para controles do Windows Forms. Há suporte somente para a ativação gerenciada de controles do Windows Forms. Depois de criar um controle do Windows Forms, você pode hospedá-lo em um aplicativo MFC assim como faz para um controle ActiveX.  
  
 Para usar controles do Windows Forms em seu aplicativo não gerenciado, hospede o CLR usando as APIs de hospedagem de CLR não gerenciadas ou use os recursos de interoperabilidade C++. A solução recomendada é usar os recursos de interoperabilidade C++.  
  
## <a name="windows-forms-in-com-client-applications"></a>Windows Forms em aplicativos cliente COM  
 Quando você abre um Formulário do Windows de um aplicativo cliente COM, como um aplicativo Visual Basic 6.0 ou um aplicativo MFC, o formulário pode se comportar de modo inesperado. Por exemplo, quando você pressiona a tecla TAB, o foco não muda de um controle para outro. Quando você pressiona a tecla ENTER enquanto um botão de comando tem o foco, o botão <xref:System.Windows.Forms.Control.Click> não é gerado. Você também pode enfrentar um comportamento inesperado de pressionamentos de teclas ou atividade do mouse.  
  
 Esse comportamento ocorre porque o aplicativo não gerenciado não implementa o suporte de loop de mensagem que o Windows Forms requer para funcionar corretamente. O loop de mensagem fornecido pelo aplicativo cliente COM é fundamentalmente diferente do loop de mensagem do Windows Forms.  
  
 Um loop de mensagem do aplicativo é um loop interno do programa que recupera mensagens da fila de mensagens do thread, converte-as e envia-as para o aplicativo para serem processadas. O loop de mensagem para um Windows Form não tem a mesma arquitetura que loops de mensagem que aplicativos anteriores, como aplicativos do Visual Basic 6.0 e do MFC, forneciam. As mensagens de janela que são lançadas para o loop de mensagem podem ser processadas de maneira diferente daquela que o Formulário do Windows espera. Portanto, pode ocorrer um comportamento inesperado. Algumas combinações de teclas e atividades do mouse podem não funcionar ou alguns eventos podem não ser gerados como o esperado.  
  
## <a name="resolving-interoperability-issues"></a>Resolvendo problemas de interoperabilidade  
 Você pode resolver esses problemas exibindo o formulário em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem, que é criado usando o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método.  
  
 Para fazer um Formulário do Windows funcionar corretamente em um aplicativo cliente COM, execute-o em um loop de mensagem do Windows Forms. Para fazer isso, use uma das abordagens a seguir:  
  
-   Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows. Para mais informações, consulte [Como dar suporte à interoperabilidade COM exibindo um Formulário do Windows Forms com o método ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Exiba cada Formulário do Windows em um novo thread. Para obter mais informações, consulte [Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="see-also"></a>Consulte também  
 [Windows Forms e Aplicativos Não Gerenciados](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)  
 [Interoperabilidade COM](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Interoperabilidade COM em Aplicativos .NET Framework](~/docs/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Exemplos de interoperabilidade COM](https://msdn.microsoft.com/library/09c38567-6380-4d70-848a-e896a4ca05f4)  
 [Aximp.exe (Importador de Controle ActiveX do Windows Forms)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md)  
 [Expondo componentes do .NET Framework ao COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Empacotando um assembly para COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Registrando assemblies usando COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Como dar suporte à interoperabilidade COM exibindo um Windows Form com o método ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
