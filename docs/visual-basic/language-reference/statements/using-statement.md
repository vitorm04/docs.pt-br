---
title: Instrução Using
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352767"
---
# <a name="using-statement-visual-basic"></a>Instrução Using (Visual Basic)

Declara o início de um bloco de `Using` e, opcionalmente, adquire os recursos do sistema que o bloco controla.

## <a name="syntax"></a>Sintaxe

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a>Partes

|Termo|Definição|  
|---|---|  
|`resourcelist`|Necessário se você não fornecer `resourceexpression`. Lista de um ou mais recursos do sistema que esse `Using` bloquear controles, separados por vírgulas.|  
|`resourceexpression`|Necessário se você não fornecer `resourcelist`. Variável ou expressão de referência que se refere a um recurso do sistema a ser controlado por este bloco de `Using`.|  
|`statements`|Opcional. Bloco de instruções que o bloco de `Using` é executado.|  
|`End Using`|Necessária. Encerra a definição do bloco de `Using` e descarta todos os recursos que ele controla.|  

 Cada recurso na parte `resourcelist` tem a seguinte sintaxe e partes:

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 - ou -

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a>Partes da resourceList

|Termo|Definição|  
|---|---|  
|`resourcename`|Necessária. Variável de referência que se refere a um recurso do sistema que o `Using` bloquear controles.|  
|`New`|Obrigatório se a instrução `Using` adquire o recurso. Se você já tiver adquirido o recurso, use a segunda sintaxe alternativa.|  
|`resourcetype`|Necessária. A classe do recurso. A classe deve implementar a interface <xref:System.IDisposable>.|  
|`arglist`|Opcional. Lista de argumentos que você está passando para o construtor para criar uma instância de `resourcetype`. Consulte a [lista de parâmetros](parameter-list.md).|  
|`resourceexpression`|Necessária. Variável ou expressão referindo-se a um recurso do sistema que atende aos requisitos de `resourcetype`. Se você usar a segunda alternativa de sintaxe, deverá adquirir o recurso antes de passar o controle para a instrução `Using`.|  
  
## <a name="remarks"></a>Comentários

 Às vezes, seu código requer um recurso não gerenciado, como um identificador de arquivo, um wrapper COM ou uma conexão SQL. Um bloco de `Using` garante a eliminação de um ou mais desses recursos quando seu código é concluído com eles. Isso os torna disponíveis para uso de outro código.

 Os recursos gerenciados são descartados pelo GC (coletor de lixo .NET Framework) sem qualquer codificação extra de sua parte. Você não precisa de um bloco de `Using` para recursos gerenciados. No entanto, você ainda pode usar um bloco de `Using` para forçar a eliminação de um recurso gerenciado em vez de aguardar o coletor de lixo.

 Um bloco de `Using` tem três partes: aquisição, uso e alienação.

- A *aquisição* significa criar uma variável e inicializá-la para se referir ao recurso do sistema. A instrução `Using` pode adquirir um ou mais recursos, ou você pode adquirir exatamente um recurso antes de inserir o bloco e fornecê-lo à instrução `Using`. Se você fornecer `resourceexpression`, deverá adquirir o recurso antes de passar o controle para a instrução `Using`.

- O *uso* significa acessar os recursos e executar ações com eles. As instruções entre `Using` e `End Using` representam o uso dos recursos.

- *Alienação* significa chamar o método <xref:System.IDisposable.Dispose%2A> no objeto em `resourcename`. Isso permite que o objeto termine corretamente seus recursos. A instrução `End Using` descarta os recursos sob o controle do bloco de `Using`.

## <a name="behavior"></a>Comportamento

 Um bloco de `Using` se comporta como uma `Try`...`Finally` construção na qual o bloco de `Try` usa os recursos e o bloco de `Finally` descarta-os. Por isso, o bloco de `Using` garante a alienação dos recursos, independentemente de como você sai do bloco. Isso é verdadeiro mesmo no caso de uma exceção sem tratamento, exceto para um <xref:System.StackOverflowException>.

 O escopo de cada variável de recurso adquirido pela instrução `Using` é limitado ao bloco de `Using`.

 Se você especificar mais de um recurso do sistema na instrução `Using`, o efeito será o mesmo que se você tiver aninhado `Using` blocos um dentro de outro.

 Se `resourcename` for `Nothing`, nenhuma chamada para <xref:System.IDisposable.Dispose%2A> será feita e nenhuma exceção será lançada.

## <a name="structured-exception-handling-within-a-using-block"></a>Manipulação de exceção estruturada dentro de um bloco Using

 Se você precisar manipular uma exceção que pode ocorrer dentro do bloco de `Using`, poderá adicionar uma construção `Try`...`Finally` completa a ela. Se você precisar lidar com o caso em que a instrução `Using` não é bem-sucedida ao adquirir um recurso, você pode testar para ver se `resourcename` está `Nothing`.

## <a name="structured-exception-handling-instead-of-a-using-block"></a>Manipulação de exceção estruturada em vez de um bloco Using

 Se precisar de um controle mais preciso sobre a aquisição dos recursos ou se precisar de código adicional no bloco de `Finally`, você poderá reescrever o bloco de `Using` como uma construção `Try`...`Finally`. O exemplo a seguir mostra `Try` de esqueleto e construções de `Using` que são equivalentes na aquisição e no descarte de `resource`.

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> O código dentro do bloco de `Using` não deve atribuir o objeto em `resourcename` a outra variável. Quando você sai do bloco de `Using`, o recurso é Descartado e a outra variável não pode acessar o recurso ao qual ele aponta.

## <a name="example"></a>Exemplo

 O exemplo a seguir cria um arquivo chamado log. txt e grava duas linhas de texto no arquivo. O exemplo também lê o mesmo arquivo e exibe as linhas de texto:

 Como as classes <xref:System.IO.TextWriter> e <xref:System.IO.TextReader> implementam a interface <xref:System.IDisposable>, o código pode usar instruções `Using` para garantir que o arquivo seja fechado corretamente após as operações de gravação e leitura.

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable>
- [Instrução Try...Catch...Finally](try-catch-finally-statement.md)
- [Como descartar um recurso do sistema](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
