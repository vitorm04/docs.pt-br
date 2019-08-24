---
title: Erros de tempo de design no Designer de Formulários do Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015965"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Erros de tempo de design no Designer de Formulários do Windows

Este tópico explica o significado e o uso da lista de erros em tempo de design que aparece no Visual Studio quando o Designer de Formulários do Windows falha ao carregar. Se essa lista de erros aparecer, não a interprete como um bug do designer, mas como um auxílio para a correção de erros no código.

Uma compreensão básica dessa lista de erros o ajudará a depurar aplicativos, fornecendo informações detalhadas sobre os erros e sugerindo possíveis soluções.

## <a name="the-design-time-error-list-interface"></a>A interface da lista de erros em tempo de design

Se a Designer de Formulários do Windows falhar ao carregar, uma lista de erros aparecerá no designer. Os erros são agrupados em categorias. Por exemplo, se houver quatro instâncias de variáveis não declaradas, eles serão agrupados na mesma categoria de erro. Cada categoria de erro inclui uma breve descrição que resume o erro.

É possível expandir ou recolher uma categoria de erro clicando no título da categoria de erro ou clicando na divisa expandir/recolher. Ao expandir uma categoria de erro, a ajuda adicional a seguir será exibida:

- Instâncias desse erro.

- Ajuda sobre esse erro.

- Postagens do fórum sobre esse erro.

### <a name="instances-of-this-error"></a>Instâncias desse erro

A ajuda adicional lista todas as instâncias do erro no projeto atual. Muitos erros incluem um local exato no seguinte formato: *[Nome do Projeto]* *[Nome do Formulário]* Linha: *[Número de Linha]* Coluna: *[Número da Coluna]* . O link **Ir para o Código** leva ao local do código em que o erro ocorre.

Se uma pilha de chamadas estiver associada ao erro, será possível clicar no link **Mostrar Pilha de Chamadas**, que expande ainda mais o erro a fim de mostrar a pilha de chamadas. Examinar a pilha pode fornecer informações de depuração valiosas. Por exemplo, é possível rastrear as funções chamadas antes da ocorrência do erro. A pilha de chamadas é selecionável para que você possa copiá-la e salvá-la.

> [!NOTE]
> No Visual Basic, a lista de erros de tempo de design não exibe mais de um erro, mas pode exibir várias instâncias do mesmo erro. No Visual C++, os erros não links/links para número de linha para o código goto.

### <a name="forum-posts-about-this-error"></a>Postagens do fórum sobre este erro

A ajuda adicional inclui um link para postagens de fórum relacionadas ao erro. Os fóruns são pesquisados com base na cadeia de caracteres da mensagem de erro. Você também pode tentar Pesquisar nos seguintes fóruns:

- [Fórum de Designer de Formulários do Windows](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [Fórum de Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a>Ignorar e continuar

É possível ignorar a condição de erro e continuar o carregamento do designer. Escolher esta ação pode resultar em comportamento inesperado. Por exemplo, os controles podem não aparecer na superfície de design.

## <a name="see-also"></a>Consulte também

- [Solução de problemas de desenvolvimento em tempo de design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [Solução de problemas de criação de controle e de componente](troubleshooting-control-and-component-authoring.md)
- [Desenvolvendo controles dos Windows Forms em tempo de design](developing-windows-forms-controls-at-design-time.md)
- [Mensagens de erro do Designer de Formulários do Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
