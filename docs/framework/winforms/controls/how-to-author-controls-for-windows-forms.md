---
title: Como criar controles para Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: 844e38fc62fc9fb04a723c1a4a8ad834e957c8ce
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178306"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Como criar controles para Windows Forms
Um controle representa um link gráfico entre o usuário e o programa. Um controle pode fornecer ou processar dados, aceitar a entrada do usuário, responder a eventos ou executar quaisquer outras funções que conectam o usuário ao aplicativo. Como um controle é essencialmente um componente com uma interface gráfica, ele pode cumprir qualquer função realizada por um componente, além de oferecer interação ao usuário. Os controles são criados para atender a objetivos específicos e a criação de controles é apenas outra tarefa de programação. Com isso em mente, as etapas a seguir representam uma visão geral do processo de criação de controles. Os links fornecem informações adicionais sobre as etapas individuais.  
  
> [!NOTE]
>  Caso queira criar um controle personalizado para usar no Web Forms, consulte [Desenvolvendo Controles de Servidores ASP.NET Personalizados](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-control"></a>Criar um controle  
  
1.  Determine o que o controle deverá realizar ou qual será o papel executado por ele no aplicativo. Os fatores a serem considerados incluem:  
  
    -   Que tipo de interface gráfica será necessária?  
  
    -   Quais as interações específicas do usuário esse controle manipulará?  
  
    -   A funcionalidade necessária é fornecida por algum dos controles existentes?  
  
    -   É possível obter a funcionalidade necessária combinando vários controles do Windows Forms?  
  
2.  Caso seja necessário um modelo de objeto para o controle, determine como a funcionalidade será distribuída ao longo do modelo de objeto e divida-a entre o controle e os subobjetos. Um modelo de objeto poderá ser útil se você estiver planejando um controle complexo ou desejar incorporar várias funcionalidades.  
  
3.  Determine o tipo de controle (por exemplo, controle de usuário, controle personalizado, controle herdado do Windows Forms) necessário. Para obter detalhes, consulte [Recomendações do Tipo de Controle](../../../../docs/framework/winforms/controls/control-type-recommendations.md) e [Variedades de Controles Personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Expresse funcionalidades como propriedades, métodos e eventos do controle e seus subobjetos ou estruturas subsidiárias e atribua níveis de acesso apropriados (por exemplo, público, protegido e assim por diante).  
  
5.  Se uma pintura personalizada for necessária para o controle, adicione código a ele. Para obter detalhes, consulte [Pintura e renderização de controle personalizado](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Se o controle herda de <xref:System.Windows.Forms.UserControl>, você pode testar seu comportamento de tempo de execução Compilando o projeto de controle e executá-lo em de **contêiner de teste de UserControl**. Para obter mais informações, consulte [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md) (Como testar o comportamento de tempo de execução de um UserControl).  
  
7.  Também é possível testar e depurar o controle criando um novo projeto, como um Aplicativo do Windows, e colocá-lo em um contêiner. Esse processo é demonstrado nas [Instruções passo a passo: criando um controle composto com o Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  Ao adicionar cada recurso, adicione recursos ao projeto de teste para praticar a nova funcionalidade.  
  
9. Repita, refinando o design.  
  
10. Empacote e implante o controle. Para obter mais detalhes, consulte [Implantando Aplicativos, Serviços e Componentes](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Consulte também  
 [Passo a passo: criando um controle de composição com o Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Passo a passo: herdando um controle dos Windows Forms com Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Como herdar da classe UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Como herdar da classe de controle](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Como herdar de controles dos Windows Forms existentes](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Como testar o comportamento de tempo de execução de um UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Variedades de controles personalizados](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
