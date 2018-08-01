---
title: Padrão de Dispose
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7bb9420d6439cff36c5cfa997152773503fbd9a
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948544"
---
# <a name="dispose-pattern"></a>Padrão de Dispose
Todos os programas adquirem um ou mais recursos do sistema, como memória, manipuladores de sistema ou conexões de banco de dados durante sua execução. Os desenvolvedores precisam ter cuidado ao usar esses recursos do sistema, porque eles devem ser liberados após ter sido adquiridas e usadas.  
  
 O CLR fornece suporte para gerenciamento automático de memória. Memória gerenciada (memória alocada usando o operador c# `new`) não precisa ser explicitamente liberados. Ele é liberado automaticamente pelo coletor de lixo (GC). Isso libera os desenvolvedores da tarefa entediante e difícil de liberação de memória e tem sido um dos principais motivos para a produtividade sem precedentes proporcionada pelo .NET Framework.  
  
 Infelizmente, a memória gerenciada é apenas um dos muitos tipos de recursos do sistema. Recursos, além de memória gerenciada ainda precisam ser liberados explicitamente e são chamados de recursos não gerenciados. O GC especificamente não foi projetado para gerenciar esses recursos não gerenciados, o que significa que a responsabilidade de gerenciar recursos não gerenciados está nas mãos dos desenvolvedores.  
  
 O CLR fornece ajuda ao liberar recursos não gerenciados. <xref:System.Object?displayProperty=nameWithType> declara um método virtual <xref:System.Object.Finalize%2A> (também chamado o finalizador) que é chamado pelo GC antes que a memória do objeto é recuperada pelo GC e pode ser substituída para liberar recursos não gerenciados. Tipos de substituem o finalizador são denominados finalizáveis tipos.  
  
 Embora os finalizadores entrarão em vigor em alguns cenários de limpeza, eles têm duas desvantagens significativas:  
  
-   O finalizador é chamado quando o GC detecta que um objeto é qualificado para a coleta. Isso ocorre em um período indeterminado depois que o recurso não é mais necessária. O atraso entre quando o desenvolvedor poderia ou deseja liberar o recurso e a hora quando o recurso, na verdade, é lançado pelo finalizador seria inaceitável em programas que adquirem vários recursos escassos (recursos que podem ser facilmente esgotados) ou em casos nos quais recursos são caros manter em uso (por exemplo, buffers de memória não gerenciada grande).  
  
-   Quando o CLR precisa chamar um finalizador, ele deve adiar a coleção de memória do objeto até que a próxima de ida e volta da coleta de lixo (os finalizadores executadas entre coleções). Isso significa que a memória do objeto (e todos os objetos que se refere a) não seja liberados para um período de tempo maior.  
  
 Portanto, depender exclusivamente finalizadores pode não ser apropriado em muitos cenários, quando é importante recuperar recursos não gerenciados assim que possível, ao lidar com recursos escassos ou em cenários de alto desempenho altamente no qual a sobrecarga adicional de GC de finalização é inaceitável.  
  
 Fornece a estrutura de <xref:System.IDisposable?displayProperty=nameWithType> interface que deve ser implementada para fornecer ao desenvolvedor uma maneira manual para liberar recursos não gerenciados, assim que eles não são necessários. Ele também fornece o <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> método que pode informar o GC um objeto manualmente foi descartado e não precisa ser finalizado, caso em que a memória do objeto pode ser recuperada anteriormente. Tipos que implementam o `IDisposable` interface são chamados de tipos descartáveis.  
  
 O padrão Dispose destina-se para padronizar o uso e a implementação de finalizadores e `IDisposable` interface.  
  
 A principal motivação para o padrão é para reduzir a complexidade da implementação do <xref:System.Object.Finalize%2A> e <xref:System.IDisposable.Dispose%2A> métodos. Reduz a complexidade do fato de que os métodos compartilham algumas, mas nem todos os caminhos de código (as diferenças são descritas posteriormente no capítulo). Além disso, há razões históricas para alguns elementos do padrão relacionadas a evolução de suporte ao idioma para o gerenciamento de recursos determinística.  
  
 **✓ DO** implementar o padrão de Dispose básico em tipos que contém instâncias de tipos descartáveis. Consulte o [padrão Dispose básico](#basic_pattern) seção para obter detalhes sobre o padrão básico.  
  
 Se um tipo é responsável pelo tempo de vida de outros objetos descartáveis, os desenvolvedores precisam de uma maneira de descartá-los, muito. Usando o contêiner `Dispose` método é uma maneira conveniente para que isso aconteça.  
  
 **✓ DO** implementar o padrão de Dispose básico e fornecer um finalizador em tipos de recursos de retenção que precisam ser liberados explicitamente e que não tenham finalizadores.  
  
 Por exemplo, o padrão deve ser implementado em tipos de armazenamento de buffers de memória não gerenciada. O [tipos finalizáveis](#finalizable_types) seção discute as diretrizes relacionadas à implementação finalizadores.  
  
 **✓ CONSIDER** Implementando o padrão de Dispose básico em classes que se não mantém os recursos não gerenciados ou objetos descartáveis mas serão prováveis que os subtipos que fazer.  
  
 Um ótimo exemplo disso é a <xref:System.IO.Stream?displayProperty=nameWithType> classe. Embora seja uma classe base abstrata que não contêm todos os recursos, a maioria de suas subclasses fazer e por isso, ele implementa esse padrão.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Padrão Dispose básico  
 A implementação básica do padrão envolve a implementação de `System.IDisposable` interface e declarando o `Dispose(bool)` método que implementa a lógica de limpeza todos os recursos para serem compartilhadas entre o `Dispose` método e o finalizador opcional.  
  
 O exemplo a seguir mostra uma implementação simples do que o padrão básico:  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder() {  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposing) {  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 O parâmetro booliano `disposing` indica se o método foi chamado a partir de `IDisposable.Dispose` implementação ou o finalizador. O `Dispose(bool)` implementação deve verificar o parâmetro antes de acessar outros objetos de referência (por exemplo, o campo de recurso no exemplo anterior). Esses objetos só devem ser acessados quando o método é chamado da `IDisposable.Dispose` implementação (quando o `disposing` parâmetro for igual a true). Se o método é invocado do finalizador (`disposing` é false), outros objetos não devem ser acessados. O motivo é que os objetos são finalizados em uma ordem imprevisível e portanto eles ou qualquer uma de suas dependências, pode já ter finalizado.  
  
 Além disso, esta seção se aplica a classes com uma base que não implementa o padrão Dispose. Se você estiver herdando de uma classe que já implementa o padrão, basta substituir a `Dispose(bool)` método para fornecer lógica de limpeza de recursos adicionais.  
  
 **✓ DO** declarar um `protected virtual void Dispose(bool disposing)` método centralizar toda a lógica relacionado à liberação de recursos não gerenciados.  
  
 Limpeza de todos os recursos deve ocorrer nesse método. O método é chamado de ambos o finalizador e `IDisposable.Dispose` método. O parâmetro será false se o que está sendo chamado de dentro de um finalizador. Ele deve ser usado para garantir que qualquer código em execução durante a finalização não está acessando a outros objetos finalizáveis. Detalhes de implementação de finalizadores são descritos na próxima seção.  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ DO** implementar o `IDisposable` interface simplesmente chamando `Dispose(true)` seguido por `GC.SuppressFinalize(this)`.  
  
 A chamada para `SuppressFinalize` deve ocorrer somente se `Dispose(true)` for executado com êxito.  
  
```csharp
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X DO NOT** fazer o sem parâmetros `Dispose` método virtual.  
  
 O `Dispose(bool)` método é o que deve ser substituído por subclasses.  
  
```csharp
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose() { ... }  
    protected virtual void Dispose(bool disposing) { ... }  
}  
```  
  
 **X DO NOT** declarar qualquer sobrecargas do `Dispose` método diferente do `Dispose()` e `Dispose(bool)`.  
  
 `Dispose` deve ser considerada uma palavra reservada para ajudar a codificar esse padrão e evitar confusão entre implementadores, usuários e compiladores. Alguns idiomas podem optar por implementar esse padrão automaticamente em determinados tipos.  
  
 **✓ DO** permitir a `Dispose(bool)` método a ser chamado mais de uma vez. O método pode optar por não fazer nada após a primeira chamada.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X AVOID** lançar uma exceção no `Dispose(bool)` exceto sob críticas situações em que o processo contendo está corrompido (vazamentos, estado compartilhado inconsistente, etc.).  
  
 Os usuários esperam que uma chamada para `Dispose` não gerará uma exceção.  
  
 Se `Dispose` pode gerar uma exceção, a lógica de limpeza de bloco finally adicional não será executado. Para contornar isso, o usuário teria que encapsulam cada chamada para `Dispose` (dentro do bloco finally!) em um bloco try, o que leva para manipuladores de limpeza muito complexos. Se a execução de um `Dispose(bool disposing)` método, nunca lançar uma exceção se disposing é false. Ao fazer isso, o processo será encerrado se a execução dentro de um contexto de finalizador.  
  
 **✓ DO** lançar um <xref:System.ObjectDisposedException> de qualquer membro que não pode ser usado depois que o objeto foi descartado.  
  
```csharp
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething() {  
        if (disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
        ...  
    }  
    protected virtual void Dispose(bool disposing) {  
        if (disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ CONSIDER** fornecendo método `Close()`, além de `Dispose()`, se fechar é terminologia padrão na área.  
  
 Ao fazer isso, é importante que você faça a `Close` implementação idêntica ao `Dispose` e considere implementar a `IDisposable.Dispose` método explicitamente.  
  
```csharp
public class Stream : IDisposable {  
    IDisposable.Dispose() {  
        Close();  
    }  
    public void Close() {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## <a name="finalizable-types"></a>Tipos finalizáveis  
 Tipos finalizáveis são tipos que estendem o padrão básico de Dispose substituir o finalizador e fornecendo o caminho de código de finalização no `Dispose(bool)` método.  
  
 Os finalizadores são notoriamente difíceis de implementar corretamente, principalmente porque você não pode fazer algumas suposições (normalmente válidas) sobre o estado do sistema durante sua execução. As diretrizes a seguir devem ser levadas em consideração cuidadosa.  
  
 Observe que algumas das diretrizes se aplicam não apenas para o `Finalize` método, mas a qualquer código chamado a partir de um finalizador. No caso de Dispose padrão básico definido anteriormente, isso significa que a lógica que é executado dentro `Dispose(bool disposing)` quando o `disposing` parâmetro for false.  
  
 Se a classe base já é finalizável e implementa o padrão de Dispose básico, você não deve substituir `Finalize` novamente. Você deve em vez disso, basta substituir a `Dispose(bool)` método para fornecer lógica de limpeza de recursos adicionais.  
  
 O código a seguir mostra um exemplo de um tipo finalizável:  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder() {  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing) {  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing) { // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    public void Dispose() {
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X AVOID** fazer tipos finalizáveis.  
  
 Considere cuidadosamente algum caso no qual você acha que é necessário um finalizador. Há um real custo associado com instâncias com finalizadores, do ponto de vista de complexidade de um desempenho e de código. Preferir usar wrappers de recursos, como <xref:System.Runtime.InteropServices.SafeHandle> para encapsular recursos não gerenciados, sempre que possível, caso em que um finalizador é desnecessário porque o wrapper é responsável por sua própria limpeza de recursos.  
  
 **X DO NOT** tornar os tipos de valor finalizáveis.  
  
 Somente os tipos de referência, na verdade, obtenham finalizados pelo CLR, e, portanto, qualquer tentativa de colocar um finalizador em um tipo de valor será ignorada. O c# e C++ compiladores impõem essa regra.  
  
 **✓ DO** fazer um tipo finalizáveis se o tipo é responsável pela liberação de um recurso não gerenciado que não tem seu próprio finalizador.  
  
 Ao implementar o finalizador, simplesmente chamar `Dispose(false)` e coloque a lógica de limpeza todos os recursos dentro de `Dispose(bool disposing)` método.  
  
```csharp
public class ComplexResourceHolder : IDisposable {  
  
    ~ComplexResourceHolder() {
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing) {
        ...  
    }  
}  
```  
  
 **✓ DO** implementar o padrão de Dispose básico em cada tipo finalizável.  
  
 Isso fornece aos usuários do tipo um meio para executar explicitamente a limpeza determinística desses recursos mesmo para os quais o finalizador é responsável.  
  
 **X DO NOT** acessar quaisquer objetos finalizáveis no caminho de código do finalizador, porque não há risco significativo que eles serão já ter sido finalizados.  
  
 Por exemplo, um objeto finalizável A que tem uma referência a outro objeto finalizável B confiável não é possível usar B do finalizador, ou vice-versa. Os finalizadores são chamados em uma ordem aleatória (com pouca uma garantia de ordenação fraca finalização crítico).  
  
 Além disso, lembre-se de que os objetos armazenados em variáveis estáticas obter coletados em determinados pontos durante um descarregamento de domínio de aplicativo ou ao sair do processo. Acessando uma variável estática que se refere a um objeto finalizável (ou chamar um método estático que pode usar os valores armazenados em variáveis estáticas) pode não ser seguro se <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> retorna true.  
  
 **✓ DO** fazer sua `Finalize` método protegido.  
  
 Os desenvolvedores do c#, C++ e VB.NET não precisa se preocupar com isso, porque os compiladores de ajudam a impor essa diretriz.  
  
 **X DO NOT** escape permitem exceções da lógica finalizador, exceto para falhas críticas do sistema.  
  
 Se uma exceção é gerada a partir de um finalizador, o CLR desligará o processo inteiro (a partir do .NET Framework versão 2.0), impedindo que outros finalizadores executando e recursos do que está sendo liberado de forma controlada.  
  
 **✓ CONSIDER** criando e usando um objeto finalizável crítico (um tipo com uma hierarquia de tipo que contém <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) para situações em que um finalizador absolutamente deve executar mesmo em caso de thread e os descarregamentos de domínio de aplicativo forçada será anulada.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Padrões comuns de Design](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
