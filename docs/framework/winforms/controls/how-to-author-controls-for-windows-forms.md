---
title: 'Como: Criar Controles para o Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 45a6ae68102204ad8506027065c2676e02fdd7a3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015911"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Como: Controles de autor para Windows Forms

Um controle representa um link gráfico entre o usuário e o programa. Um controle pode fornecer ou processar dados, aceitar a entrada do usuário, responder a eventos ou executar quaisquer outras funções que conectam o usuário ao aplicativo. Como um controle é essencialmente um componente com uma interface gráfica, ele pode cumprir qualquer função realizada por um componente, além de oferecer interação ao usuário. Os controles são criados para atender a objetivos específicos e a criação de controles é apenas outra tarefa de programação. Com isso em mente, as etapas a seguir representam uma visão geral do processo de criação de controles. Os links fornecem informações adicionais sobre as etapas individuais.

## <a name="to-author-a-control"></a>Criar um controle

1. Determine o que o controle deverá realizar ou qual será o papel executado por ele no aplicativo. Os fatores a serem considerados incluem:

    - Que tipo de interface gráfica será necessária?

    - Quais as interações específicas do usuário esse controle manipulará?

    - A funcionalidade necessária é fornecida por algum dos controles existentes?

    - É possível obter a funcionalidade necessária combinando vários controles do Windows Forms?

2. Caso seja necessário um modelo de objeto para o controle, determine como a funcionalidade será distribuída ao longo do modelo de objeto e divida-a entre o controle e os subobjetos. Um modelo de objeto poderá ser útil se você estiver planejando um controle complexo ou desejar incorporar várias funcionalidades.

3. Determine o tipo de controle (por exemplo, controle de usuário, controle personalizado, controle herdado do Windows Forms) necessário. Para obter detalhes, consulte [Recomendações do Tipo de Controle](control-type-recommendations.md) e [Variedades de Controles Personalizados](varieties-of-custom-controls.md).

4. Expresse funcionalidades como propriedades, métodos e eventos do controle e seus subobjetos ou estruturas subsidiárias e atribua níveis de acesso apropriados (por exemplo, público, protegido e assim por diante).

5. Se uma pintura personalizada for necessária para o controle, adicione código a ele. Para obter detalhes, consulte [Pintura e renderização de controle personalizado](custom-control-painting-and-rendering.md).

6. Se o controle for herdado de <xref:System.Windows.Forms.UserControl>, você poderá testar seu comportamento de tempo de execução criando o projeto de controle e executando-o no contêiner de teste de **UserControl**. Para obter mais informações, confira [Como: Testar o comportamento de tempo de execução de um](how-to-test-the-run-time-behavior-of-a-usercontrol.md)UserControl.

7. Também é possível testar e depurar o controle criando um novo projeto, como um Aplicativo do Windows, e colocá-lo em um contêiner. Esse processo é demonstrado como parte [do passo a passos: Criação de um controle](walkthrough-authoring-a-composite-control-with-visual-csharp.md)composto.

8. Ao adicionar cada recurso, adicione recursos ao projeto de teste para praticar a nova funcionalidade.

9. Repita, refinando o design.

10. Empacote e implante o controle. Para obter detalhes, consulte [primeira olhada na implantação no Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="see-also"></a>Consulte também

- [Como: Herdar da classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Como: Herdar da classe de controle](how-to-inherit-from-the-control-class.md)
- [Como: Herdar de controles de Windows Forms existentes](how-to-inherit-from-existing-windows-forms-controls.md)
- [Como: Testar o comportamento de tempo de execução de um UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Variedades de controles personalizados](varieties-of-custom-controls.md)
