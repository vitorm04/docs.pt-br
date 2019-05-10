---
title: 'Como: Criar Controles para o Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: 8adc9644f987166729c43b79a6891960978341dd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612723"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Como: Criar Controles para o Windows Forms
Um controle representa um link gráfico entre o usuário e o programa. Um controle pode fornecer ou processar dados, aceitar a entrada do usuário, responder a eventos ou executar quaisquer outras funções que conectam o usuário ao aplicativo. Como um controle é essencialmente um componente com uma interface gráfica, ele pode cumprir qualquer função realizada por um componente, além de oferecer interação ao usuário. Os controles são criados para atender a objetivos específicos e a criação de controles é apenas outra tarefa de programação. Com isso em mente, as etapas a seguir representam uma visão geral do processo de criação de controles. Os links fornecem informações adicionais sobre as etapas individuais.  
  
> [!NOTE]
>  Caso queira criar um controle personalizado para usar no Web Forms, consulte [Desenvolvendo Controles de Servidores ASP.NET Personalizados](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
>   
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, confira [Personalizar o IDE do Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-author-a-control"></a>Criar um controle  
  
1. Determine o que o controle deverá realizar ou qual será o papel executado por ele no aplicativo. Os fatores a serem considerados incluem:  
  
    - Que tipo de interface gráfica será necessária?  
  
    - Quais as interações específicas do usuário esse controle manipulará?  
  
    - A funcionalidade necessária é fornecida por algum dos controles existentes?  
  
    - É possível obter a funcionalidade necessária combinando vários controles do Windows Forms?  
  
2. Caso seja necessário um modelo de objeto para o controle, determine como a funcionalidade será distribuída ao longo do modelo de objeto e divida-a entre o controle e os subobjetos. Um modelo de objeto poderá ser útil se você estiver planejando um controle complexo ou desejar incorporar várias funcionalidades.  
  
3. Determine o tipo de controle (por exemplo, controle de usuário, controle personalizado, controle herdado do Windows Forms) necessário. Para obter detalhes, consulte [Recomendações do Tipo de Controle](control-type-recommendations.md) e [Variedades de Controles Personalizados](varieties-of-custom-controls.md).  
  
4. Expresse funcionalidades como propriedades, métodos e eventos do controle e seus subobjetos ou estruturas subsidiárias e atribua níveis de acesso apropriados (por exemplo, público, protegido e assim por diante).  
  
5. Se uma pintura personalizada for necessária para o controle, adicione código a ele. Para obter detalhes, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).  
  
6. Se o controle herda de <xref:System.Windows.Forms.UserControl>, você pode testar seu comportamento de tempo de execução Compilando o projeto de controle e executá-lo em de **contêiner de teste de UserControl**. Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7. Também é possível testar e depurar o controle criando um novo projeto, como um Aplicativo do Windows, e colocá-lo em um contêiner. Esse processo é demonstrado como parte do [passo a passo: Criando um controle composto com o Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8. Ao adicionar cada recurso, adicione recursos ao projeto de teste para praticar a nova funcionalidade.  
  
9. Repita, refinando o design.  
  
10. Empacote e implante o controle. Para obter detalhes, consulte [Introdução à implantação no Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).  
  
## <a name="see-also"></a>Consulte também

- [Passo a passo: Criando um controle composto com o Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Passo a passo: Herdando um controle de formulários do Windows com o Visual Basic](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [Como: Herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Como: Herdar da classe de controle](how-to-inherit-from-the-control-class.md)
- [Como: Herdar controles de formulários do Windows existentes](how-to-inherit-from-existing-windows-forms-controls.md)
- [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Variedades de controles personalizados](varieties-of-custom-controls.md)
