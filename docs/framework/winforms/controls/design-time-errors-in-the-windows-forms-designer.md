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
ms.openlocfilehash: ec1801a1b695867a7edcd99394feebe1d0f6853a
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46531741"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Erros de tempo de design no Designer de Formulários do Windows
Este tópico explica o significado e o uso da lista de erros de tempo de design que aparece no Microsoft Visual Studio quando o carregamento do Designer de Formulários do Windows falha. Se essa lista de erros aparecer, não a interprete como um bug do designer, mas como um auxílio para a correção de erros no código.  
  
 Uma compreensão básica dessa lista de erros o ajudará a depurar aplicativos, fornecendo informações detalhadas sobre os erros e sugerindo possíveis soluções.  
  
## <a name="the-design-time-error-list-interface"></a>A Interface de Lista de Erros de Tempo de Design  
 Se o carregamento do Designer de Formulários do Windows falhar, uma lista de erros aparecerá no designer. Os erros são agrupados em categorias. Por exemplo, se houver quatro instâncias de variáveis não declaradas, eles serão agrupados na mesma categoria de erro. Cada categoria de erro inclui uma breve descrição que resume o erro.  
  
 É possível expandir ou recolher uma categoria de erro clicando no título da categoria de erro ou clicando na divisa expandir/recolher. Ao expandir uma categoria de erro, a ajuda adicional a seguir será exibida:  
  
-   Instâncias desse erro.  
  
-   Ajuda sobre esse erro.  
  
-   Postagens do fórum sobre esse erro.  
  
### <a name="instances-of-this-error"></a>Instâncias Desse Erro  
 A ajuda adicional lista todas as instâncias do erro no projeto atual. Muitos erros incluem um local exato no seguinte formato: *[Nome do Projeto]* *[Nome do Formulário]* Linha:*[Número de Linha]* Coluna:*[Número da Coluna]*. O link **Ir para o Código** leva ao local do código em que o erro ocorre.  
  
 Se uma pilha de chamadas estiver associada ao erro, será possível clicar no link **Mostrar Pilha de Chamadas**, que expande ainda mais o erro a fim de mostrar a pilha de chamadas. Examinar a pilha pode fornecer informações de depuração valiosas. Por exemplo, é possível rastrear as funções chamadas antes da ocorrência do erro. A pilha de chamadas é selecionável para que você possa copiá-la e salvá-la.  
  
> [!NOTE]
>  No Visual Basic, a lista de erros de tempo de design não exibe mais de um erro, mas pode exibir várias instâncias do mesmo erro. No Visual C++, os erros não links/links para número de linha para o código goto.  
  
### <a name="help-with-this-error"></a>Ajuda com esse erro  
 Se o erro contiver um link para um tópico de ajuda associado do MSDN, a ajuda adicional incluirá um link para o tópico de ajuda. Ao clicar no link, o tópico de ajuda associado aparecerá no Visual Studio.  
  
### <a name="forum-posts-about-this-error"></a>Postagens do fórum sobre este erro  
 A ajuda adicional incluirá um link para postagens no fórum do MSDN relacionadas ao erro. Os fóruns são pesquisados com base na cadeia de caracteres da mensagem de erro. Também é possível tentar pesquisar os fóruns a seguir:  
  
-   [Fórum do Designer de Formulários do Windows](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Fóruns do Windows Forms](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>Ignorar e Continuar  
 É possível ignorar a condição de erro e continuar o carregamento do designer. Escolher esta ação pode resultar em comportamento inesperado. Por exemplo, os controles podem não aparecer na superfície de design.  
  
## <a name="see-also"></a>Consulte também  
 [Solucionando problemas de desenvolvimento de tempo de Design](https://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [Solução de problemas de criação de controle e de componente](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 [Desenvolvendo controles dos Windows Forms em tempo de design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Mensagens de erro do Designer de Formulários do Windows](https://msdn.microsoft.com/library/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)
