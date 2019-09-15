---
title: Usando o contexto de edição de ModelItem
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a47cb53e50d221c0ae07cf0841688fe4f8ced7d4
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988915"
---
# <a name="using-the-modelitem-editing-context"></a>Usando o contexto de edição de ModelItem
<xref:System.Activities.Presentation.Model.ModelItem> que contexto de edição é o objeto que o aplicativo host usa para se comunicar com o designer. <xref:System.Activities.Presentation.EditingContext> expõe dois métodos, <xref:System.Activities.Presentation.EditingContext.Items%2A> e <xref:System.Activities.Presentation.EditingContext.Services%2A>, que podem ser usados  
  
## <a name="the-items-collection"></a>A coleção de itens  
 A coleção de <xref:System.Activities.Presentation.EditingContext.Items%2A> é usada para acessar os dados que são compartilhados entre o host e o designer, ou os dados que estão disponíveis para todos os designers. Essa coleção possui os seguintes recursos, acessados por meio da classe <xref:System.Activities.Presentation.ContextItemManager> :  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>A coleção de serviços  
 A coleção de <xref:System.Activities.Presentation.EditingContext.Services%2A> é usada para acessar os serviços que o designer usa para interagir com o host, ou serviços que todos os designers usam. Esta coleção tem os seguintes métodos de observação:  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>Atribuindo a um designer uma atividade  
 Para especificar que o designer uma atividade, use o atributo de designer é usado.  
  
```csharp  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{
}
```  
  
## <a name="creating-a-service"></a>Criando um serviço  
 Para criar um serviço que os serve como uma canalização de informações entre o designer e o host, uma interface e uma implementação deve ser criados. A interface é usada pelo método de <xref:System.Activities.Presentation.ServiceManager.Publish%2A> para definir os membros de serviço, e a implementação contém a lógica para o serviço. No exemplo de código, uma interface e uma implementação de serviço são criadas.  
  
```csharp  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {   
                DisplayName + " One",   
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a>Publicando um serviço  
 Para que um designer consome um serviço, deve primeiro ser publicados pelo host que usa o método de <xref:System.Activities.Presentation.ServiceManager.Publish%2A> .  
  
```csharp  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>Assinar um serviço  
 O designer obtém o acesso ao serviço usando o método de <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> no método de <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> . O snippet de código a seguir demonstra como assinar um serviço.  
  
```csharp  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;   
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a>Compartilhando dados usando a coleção de itens  
 Usar a coleção de itens é semelhante a usar a coleção de serviços, exceto que <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> é usado em vez de publicação. Essa coleção é mais adequado para compartilhar dados simples entre os designers e o host, em vez de funcionalidades complexas.  
  
## <a name="editingcontext-host-items-and-services"></a>Itens e serviços de host de EditingContext  
 O .NET Framework fornece vários itens e serviços internos acessados por meio do contexto de edição.  
  
 Itens:  
  
- <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Gerencia a lista de assemblies locais referenciados que serão usados dentro do fluxo de trabalho para controles (como o editor de expressão).  
  
- <xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indica se o designer está em um estado somente leitura.  
  
- <xref:System.Activities.Presentation.View.Selection>: Define a coleção de objetos selecionados atualmente.  
  
- <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
- <xref:System.Activities.Presentation.WorkflowFileItem>: Fornece informações sobre o arquivo no qual a sessão de edição atual se baseia.  
  
 Serviços:  
  
- <xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Permite que as propriedades sejam adicionadas à instância atual, <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>usando.  
  
- <xref:System.Activities.Presentation.View.DesignerView>: Permite o acesso às propriedades da tela do designer.  
  
- <xref:System.Activities.Presentation.IActivityToolboxService>: Permite que o conteúdo da caixa de ferramentas seja atualizado.  
  
- <xref:System.Activities.Presentation.Hosting.ICommandService>: Usado para integrar comandos de designer (como o menu de contexto) com implementações de serviço fornecidas de forma personalizada.  
  
- <xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Fornece a funcionalidade para o depurador do designer.  
  
- <xref:System.Activities.Presentation.View.IExpressionEditorService>: Fornece acesso à caixa de diálogo Editor de expressão.  
  
- <xref:System.Activities.Presentation.IIntegratedHelpService>: Fornece o designer com funcionalidade de ajuda integrada.  
  
- <xref:System.Activities.Presentation.Validation.IValidationErrorService>: Fornece acesso a erros de validação <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>usando o.  
  
- <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Fornece um serviço interno para armazenar e recuperar dados. Esse serviço é usado internamente pelo .NET Framework e não se destina ao uso externo.  
  
- <xref:System.Activities.Presentation.IXamlLoadErrorService>: Fornece acesso à coleção de erros de carregamento XAML <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>usando.  
  
- <xref:System.Activities.Presentation.Services.ModelService>: Usado pelo designer para interagir com o modelo do fluxo de trabalho que está sendo editado.  
  
- <xref:System.Activities.Presentation.Model.ModelTreeManager>: Fornece acesso à raiz da árvore de itens de modelo usando <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.  
  
- <xref:System.Activities.Presentation.UndoEngine>: Fornece funcionalidade de desfazer e refazer.  
  
- <xref:System.Activities.Presentation.Services.ViewService>: Mapeia elementos visuais para itens de modelo subjacentes.  
  
- <xref:System.Activities.Presentation.View.ViewStateService>: Armazena os Estados de exibição para itens de modelo.  
  
- <xref:System.Activities.Presentation.View.VirtualizedContainerService>: Usado para personalizar o comportamento da interface do usuário do contêiner virtual.  
  
- <xref:System.Activities.Presentation.Hosting.WindowHelperService>: Usado para registrar e cancelar o registro de delegados para notificações de eventos. Também permite que um proprietário da janela é definido.
