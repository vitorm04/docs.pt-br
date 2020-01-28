---
title: Dimensionamento automático
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 96dbbb5ed20027e25f1bde89748710766ec06506
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732382"
---
# <a name="automatic-scaling-in-windows-forms"></a>Dimensionamento automático no Windows Forms

O dimensionamento automático permite que um formulário e seus controles, projetados em um computador com determinada resolução de vídeo ou fonte do sistema, sejam exibidos adequadamente em outra máquina com uma resolução de vídeo diferente ou fonte do sistema. Garante que o formulário e seus controles sejam redimensionados de forma inteligente para serem consistentes com o Windows nativo e outros aplicativos nas máquinas dos usuários e de outros desenvolvedores. O suporte do .NET Framework para dimensionamento automático e estilos visuais permite que .NET Framework aplicativos mantenham uma aparência consistente em comparação com os aplicativos nativos do Windows na máquina de cada usuário.

Na maior parte, o dimensionamento automático funciona conforme o esperado no .NET Framework versão 2,0 e posterior. No entanto, as alterações no esquema de fontes podem ser problemáticas. Para obter um exemplo de como resolver isso, consulte [como responder a alterações de esquema de fonte em um aplicativo Windows Forms](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Necessidade de dimensionamento automático

Sem o dimensionamento automático, um aplicativo criado para uma resolução ou fonte de vídeo parecerá muito pequeno ou muito grande quando a resolução ou a fonte for alterada. Por exemplo, se o aplicativo for projetado usando o ponto Tahoma 9 como uma linha de base, sem ajuste, ele aparecerá muito pequeno se for executado em um computador em que a fonte do sistema for Tahoma 12 Point. Elementos de texto, como títulos, menus, conteúdo de caixa de texto e assim por diante, serão processados menores do que outros aplicativos. Além disso, o tamanho dos elementos da interface do usuário que contêm texto, como a barra de título, os menus e muitos controles, dependem da fonte usada. Neste exemplo, esses elementos também serão relativamente menores.

Uma situação análoga ocorre quando um aplicativo é projetado para uma determinada resolução de vídeo. A resolução de vídeo mais comum é de 96 pontos por polegada (DPI), que é igual a 100% de escala de exibição, mas a resolução mais alta é exibida com suporte a 125%, 150%, 200% (que, respectivamente, igual a 120, 144 e 192 DPI) e acima estão se tornando mais comuns. Sem ajuste, um aplicativo, especialmente um baseado em gráficos, projetado para uma resolução aparecerá muito grande ou muito pequeno quando executado em outra resolução.

O dimensionamento automático busca amenizar esses problemas redimensionando automaticamente o formulário e seus controles filho de acordo com o tamanho relativo da fonte ou a resolução da tela. O sistema operacional Windows dá suporte ao dimensionamento automático de caixas de diálogo usando uma unidade relativa de medida chamada unidades de caixa de diálogo. Uma unidade de caixa de diálogo é baseada na fonte do sistema e sua relação com os pixels pode ser determinada, embora a função do SDK do Win32 `GetDialogBaseUnits`. Quando um usuário altera o tema usado pelo Windows, todas as caixas de diálogo são ajustadas automaticamente de acordo. Além disso, o .NET Framework dá suporte ao dimensionamento automático de acordo com a fonte do sistema padrão ou a resolução de vídeo. Opcionalmente, o dimensionamento automático pode ser desabilitado em um aplicativo.

## <a name="original-support-for-automatic-scaling"></a>Suporte original para dimensionamento automático

As versões 1,0 e 1,1 do .NET Framework o dimensionamento automático com suporte de uma maneira simples que dependia da fonte padrão do Windows usada para a interface do usuário, representada pelo valor do SDK do Win32 **DEFAULT_GUI_FONT**. Essa fonte geralmente é alterada apenas quando a resolução de vídeo muda. O mecanismo a seguir foi usado para implementar o dimensionamento automático:

1. No momento do design, a propriedade <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (que agora está preterida) foi definida com a altura e a largura da fonte padrão do sistema no computador do desenvolvedor.

2. Em tempo de execução, a fonte padrão do sistema do computador do usuário foi usada para inicializar a propriedade <xref:System.Windows.Forms.Control.Font%2A> da classe <xref:System.Windows.Forms.Form>.

3. Antes de exibir o formulário, o método <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> foi chamado para dimensionar o formulário. Esse método calculou os tamanhos de escala relativos de <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> e <xref:System.Windows.Forms.Control.Font%2A>, em seguida, chamou o método <xref:System.Windows.Forms.Control.Scale%2A> para realmente dimensionar o formulário e seus filhos.

4. O valor de <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> foi atualizado para que as chamadas subsequentes para <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> não redimensionem progressivamente o formulário.

Embora esse mecanismo fosse suficiente para a maioria das finalidades, ele sofreu as seguintes limitações:

- Como a propriedade <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> representa o tamanho da fonte da linha de base como valores inteiros, ocorrem erros de arredondamento que se tornam evidentes quando um formulário é alternado por várias resoluções.

- O dimensionamento automático foi implementado apenas na classe <xref:System.Windows.Forms.Form>, não na classe <xref:System.Windows.Forms.ContainerControl>. Como resultado, os controles de usuário seriam dimensionados corretamente somente quando o controle de usuário foi projetado na mesma resolução que o formulário e foi colocado no formulário em tempo de design.

- Os formulários e seus controles filho só poderiam ser projetados simultaneamente por vários desenvolvedores se suas resoluções de computador fossem as mesmas. Da mesma forma, ele também tornou a herança de um formulário dependente da resolução associada ao formulário pai.

- Ele não é compatível com os gerenciadores de layout mais recentes introduzidos com a versão 2,0 do .NET Framework, como <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>.

- Ele não oferece suporte ao dimensionamento baseado diretamente na resolução de vídeo necessária para a compatibilidade com o .NET Compact Framework.

Embora esse mecanismo seja preservado no .NET Framework versão 2,0 para manter a compatibilidade com versões anteriores, ele foi substituído pelo mecanismo de dimensionamento mais robusto descrito a seguir. Como consequência, a <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>e determinadas sobrecargas de <xref:System.Windows.Forms.Control.Scale%2A> são marcadas como obsoletas.

> [!NOTE]
> Você pode excluir com segurança as referências a esses membros ao atualizar seu código herdado para a versão .NET Framework 2,0.

## <a name="current-support-for-automatic-scaling"></a>Suporte atual para dimensionamento automático

O .NET Framework versão 2,0 vence as limitações anteriores, introduzindo as seguintes alterações no dimensionamento automático de Windows Forms:

- O suporte base para dimensionamento foi movido para a classe <xref:System.Windows.Forms.ContainerControl> de forma que todos os formulários, controles compostos nativos e controles de usuário recebam suporte de dimensionamento uniforme. Os novos membros <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> e <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> foram adicionados.

- A classe <xref:System.Windows.Forms.Control> também tem vários novos membros que permitem que ele participe do dimensionamento e ofereça suporte ao dimensionamento misto no mesmo formato. Especificamente, os membros <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>e <xref:System.Windows.Forms.Control.GetScaledBounds%2A> dão suporte ao dimensionamento.

- O suporte para dimensionamento com base na resolução da tela foi adicionado para complementar o suporte à fonte do sistema, conforme definido pela enumeração de <xref:System.Windows.Forms.AutoScaleMode>. Esse modo é compatível com o dimensionamento automático com suporte no .NET Compact Framework permitindo uma migração de aplicativo mais fácil.

- A compatibilidade com gerenciadores de layout, como <xref:System.Windows.Forms.FlowLayoutPanel> e <xref:System.Windows.Forms.TableLayoutPanel>, foi adicionada à implementação do dimensionamento automático.

- Os fatores de dimensionamento agora são representados como valores de ponto flutuante, normalmente usando a estrutura <xref:System.Drawing.SizeF>, de forma que os erros de arredondamento tenham sido praticamente eliminados.

> [!CAUTION]
> Não há suporte para mesclagens arbitrárias de DPI e modos de dimensionamento de fonte. Embora você possa dimensionar um controle de usuário usando um modo (por exemplo, DPI) e colocá-lo em um formulário usando outro modo (fonte) sem problemas, mas misturar um formulário base em um modo e um formulário derivado em outro pode levar a resultados inesperados.

### <a name="automatic-scaling-in-action"></a>Dimensionamento automático em ação

O Windows Forms agora usa a seguinte lógica para dimensionar automaticamente os formulários e seus conteúdos:

1. Em tempo de design, cada <xref:System.Windows.Forms.ContainerControl> registra o modo de dimensionamento e a resolução atual no <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> e <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, respectivamente.

2. Em tempo de execução, a resolução real é armazenada na propriedade <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A>. A propriedade <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> calcula dinamicamente a taxa entre a resolução de escala de tempo de execução e de design.

3. Quando o formulário for carregado, se os valores de <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> e <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> forem diferentes, o método <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> será chamado para dimensionar o controle e seus filhos. Esse método suspende o layout e chama o método <xref:System.Windows.Forms.Control.Scale%2A> para executar o dimensionamento real. Posteriormente, o valor de <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> é atualizado para evitar o dimensionamento progressivo.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> também é invocada automaticamente nas seguintes situações:

    - Em resposta ao evento <xref:System.Windows.Forms.Control.OnFontChanged%2A> se o modo de dimensionamento for <xref:System.Windows.Forms.AutoScaleMode.Font>.

    - Quando o layout do controle de contêiner é retomado e uma alteração é detectada nas propriedades <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> ou <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>.

    - Como implícito acima, quando um <xref:System.Windows.Forms.ContainerControl> pai está sendo dimensionado. Cada controle de contêiner é responsável por dimensionar seus filhos usando seus próprios fatores de dimensionamento e não aquele de seu contêiner pai.

5. Os controles filho podem modificar seu comportamento de dimensionamento por vários meios:

    - A propriedade <xref:System.Windows.Forms.Control.ScaleChildren%2A> pode ser substituída para determinar se os controles filho devem ser dimensionados ou não.

    - O método <xref:System.Windows.Forms.Control.GetScaledBounds%2A> pode ser substituído para ajustar os limites para os quais o controle é dimensionado, mas não a lógica de dimensionamento.

    - O método <xref:System.Windows.Forms.Control.ScaleControl%2A> pode ser substituído para alterar a lógica de dimensionamento do controle atual.

## <a name="see-also"></a>Veja também

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Renderizando controles com estilos visuais](./controls/rendering-controls-with-visual-styles.md)
- [Como Melhorar o Desempenho Evitando a Colocação em Escala Automática](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
