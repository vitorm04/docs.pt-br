### <a name="some-workflow-drag-and-drop-apis-are-obsolete"></a>Algumas APIs arrastar e soltar do Fluxo de Trabalho estão obsoletas

|   |   |
|---|---|
|Detalhes|A API Arrastar/Soltar do Fluxo de Trabalho está obsoleta e vai gerar avisos do compilador se o aplicativo for recompilado na versão 4.5.|
|Sugestão|No lugar, devem ser usadas as novas APIs <xref:System.Activities.Presentation.DragDropHelper?displayProperty=name> compatíveis com operações com vários objetos. Como alternativa, os avisos de compilação podem ser suprimidos ou evitados usando um compilador mais antigo. Ainda há suporte para as APIs.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.Activities.Presentation.DragDropHelper.DoDragMove(System.Activities.Presentation.WorkflowViewElement,System.Windows.Point)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetCompositeView(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDraggedModelItem(System.Windows.DragEventArgs)?displayProperty=nameWithType></li><li><xref:System.Activities.Presentation.DragDropHelper.GetDroppedObject(System.Windows.DependencyObject,System.Windows.DragEventArgs,System.Activities.Presentation.EditingContext)?displayProperty=nameWithType></li></ul>|

