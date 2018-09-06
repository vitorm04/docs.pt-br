---
title: Padrão de descarte
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
ms.openlocfilehash: ff52e17cfe4a4236e4d165c0961ca3a23fed9a72
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864638"
---
# <a name="dispose-pattern"></a>Padrão de descarte
Todos os programas adquirem um ou mais recursos do sistema, como memória, identificadores do sistema ou conexões de banco de dados durante o curso de sua execução. Os desenvolvedores precisam ter cuidado ao usar esses recursos do sistema, porque eles devem ser liberados depois que eles foram adquiridos e usados.  
  
 O CLR fornece suporte para gerenciamento automático de memória. Memória gerenciada (memória alocada usando o operador c# `new`) não precisa ser explicitamente liberados. Ele é liberado automaticamente pelo coletor de lixo (GC). Isso libera os desenvolvedores da tarefa entediante e difícil de liberação de memória e tem sido uma das principais razões para a produtividade sem precedentes proporcionada pelo .NET Framework.  
  
 Infelizmente, a memória gerenciada é apenas um dos muitos tipos de recursos do sistema. Recursos, além de memória gerenciada ainda precisam ser liberados explicitamente e são chamados de recursos não gerenciados. O GC especificamente não foi projetado para gerenciar esses recursos não gerenciados, o que significa que a responsabilidade de gerenciar recursos não gerenciados se encontra nas mãos dos desenvolvedores.  
  
 O CLR fornece alguma ajuda para liberar recursos não gerenciados. <xref:System.Object?displayProperty=nameWithType> declara um método virtual <xref:System.Object.Finalize%2A> (também chamado de finalizador) que é chamado pelo GC antes que a memória do objeto seja recuperada pelo GC e pode ser substituída para liberar recursos não gerenciados. Tipos que substituem o finalizador são chamados de tipos finalizáveis.  
  
 Embora os finalizadores são eficazes em alguns cenários de limpeza, eles têm duas desvantagens significativas:  
  
-   O finalizador é chamado quando o GC detecta que um objeto está qualificado para coleta. Isso ocorre em um período indeterminado depois que o recurso não é mais necessária. O atraso entre quando o desenvolvedor poderia ou gostaria de liberar o recurso e a hora quando o recurso, na verdade, é liberado pelo finalizador pode ser inaceitável em programas que adquiram vários recursos escassos (recursos que podem ser facilmente esgotados) ou em casos nos quais recursos são caros de manter em uso (por exemplo, buffers de memória não gerenciada grande).  
  
-   Quando o CLR precisa chamar um finalizador, ele deve adiar a coleta de memória do objeto até que a próxima rodada de coleta de lixo (os finalizadores executadas entre coleções). Isso significa que a memória do objeto (e todos os objetos que ele se refere a) não seja liberados por um período maior de tempo.  
  
 Portanto, depender exclusivamente de finalizadores pode não ser apropriado em muitos cenários, quando é importante recuperar os recursos não gerenciados assim que possível, ao lidar com recursos escassos, ou em cenários de alto desempenho altamente nos quais a sobrecarga de GC adicionada de finalização é inaceitável.  
  
 O Framework fornece o <xref:System.IDisposable?displayProperty=nameWithType> interface que deve ser implementada para fornecer ao desenvolvedor uma maneira manual para liberar recursos não gerenciados, assim que eles não são necessários. Ele também fornece o <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> método que pode dizer ao GC que um objeto foi descartado manualmente e não precisa ser finalizado, caso em que a memória do objeto a ser recuperada anteriormente. Tipos que implementam o `IDisposable` interface são chamados de tipos descartáveis.  
  
 O padrão Dispose destina-se a padronizar o uso e a implementação de finalizadores e a `IDisposable` interface.  
  
 A principal motivação para o padrão é reduzir a complexidade da implementação do <xref:System.Object.Finalize%2A> e o <xref:System.IDisposable.Dispose%2A> métodos. A complexidade origina-se do fato de que os métodos de compartilham algumas, mas nem todos os caminhos de código (as diferenças são descritas posteriormente neste capítulo). Além disso, há razões históricas para alguns elementos do padrão relacionadas à evolução do suporte ao idioma para o gerenciamento de recursos determinística.  
  
 **✓ DO** implementar o padrão de Dispose básico em tipos que contém instâncias de tipos descartáveis. Consulte a [padrão de descarte básico](#basic_pattern) seção para obter detalhes sobre o padrão básico.  
  
 Se um tipo é responsável pelo tempo de vida de outros objetos descartáveis, os desenvolvedores precisam de uma maneira para descartá-los, muito. Usando o contêiner `Dispose` método é uma maneira conveniente para tornar isso possível.  
  
 **✓ DO** implementar o padrão de Dispose básico e fornecer um finalizador em tipos de recursos de retenção que precisam ser liberados explicitamente e que não tenham finalizadores.  
  
 Por exemplo, o padrão deve ser implementado em tipos de armazenamento de buffers de memória não gerenciada. O [finalizáveis tipos](#finalizable_types) seção discute as diretrizes relacionadas para implementar os finalizadores.  
  
 **✓ CONSIDER** Implementando o padrão de Dispose básico em classes que se não mantém os recursos não gerenciados ou objetos descartáveis mas serão prováveis que os subtipos que fazer.  
  
 Um bom exemplo disso é o <xref:System.IO.Stream?displayProperty=nameWithType> classe. Embora seja uma classe base abstrata que não contêm todos os recursos, a maioria de suas subclasses fazer e por isso, ele implementa esse padrão.  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>Padrão de descarte básico  
 A implementação básica do padrão envolve a implementação de `System.IDisposable` interface e declarando o `Dispose(bool)` método que implementa a lógica de limpeza todos os recursos sejam compartilhados entre o `Dispose` método e o finalizador opcional.  
  
 O exemplo a seguir mostra uma implementação simples do padrão básico:  
  
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
  
 O parâmetro booliano `disposing` indica se o método foi chamado do `IDisposable.Dispose` implementação ou do finalizador. O `Dispose(bool)` implementação deve verificar o parâmetro antes de acessar outros objetos de referência (por exemplo, o campo de recurso no exemplo anterior). Esses objetos devem ser acessados somente quando o método é chamado do `IDisposable.Dispose` implementação (quando o `disposing` parâmetro é igual a true). Se o método é invocado a partir do finalizador (`disposing` é false), outros objetos não devem ser acessados. O motivo é que os objetos são finalizados em uma ordem imprevisível e então eles ou qualquer uma de suas dependências, talvez já tiverem sido finalizadas.  
  
 Além disso, esta seção se aplica às classes com uma base que não implementa o padrão Dispose. Se você estiver herdando de uma classe que já implementa o padrão, basta substituir o `Dispose(bool)` método para fornecer a lógica de limpeza de recursos adicionais.  
  
 **✓ DO** declarar um `protected virtual void Dispose(bool disposing)` método centralizar toda a lógica relacionado à liberação de recursos não gerenciados.  
  
 Limpeza de todos os recursos deve ocorrer nesse método. O método é chamado de ambos os o finalizador e o `IDisposable.Dispose` método. O parâmetro será false se o que está sendo invocado de dentro de um finalizador. Ele deve ser usado para garantir que qualquer código em execução durante a finalização não está acessando a outros objetos finalizáveis. Detalhes de como implementar os finalizadores são descritos na próxima seção.  
  
```csharp
protected virtual void Dispose(bool disposing) {  
    if (disposing) {  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ DO** implementar o `IDisposable` interface simplesmente chamando `Dispose(true)` seguido por `GC.SuppressFinalize(this)`.  
  
 A chamada para `SuppressFinalize` só deve ocorrer se `Dispose(true)` for executado com êxito.  
  
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
  
 `Dispose` deve ser considerada uma palavra reservada para ajudar a codificar esse padrão e evitar a confusão entre os implementadores, usuários e compiladores. Algumas linguagens podem optar por implementar automaticamente esse padrão em determinados tipos.  
  
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
  
 Se `Dispose` poderia gerar uma exceção, a lógica de limpeza adicional do bloco finally não será executado. Para resolver esse problema, o usuário precisaria encapsular todas as chamadas para `Dispose` (dentro do bloco finally!) em um bloco try, que leva a manipuladores de limpeza muito complexas. Se a execução de um `Dispose(bool disposing)` método, nunca lançar uma exceção se disposing é false. Ao fazer isso, o processo será encerrado se a execução dentro do contexto de um finalizador.  
  
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
  
 Ao fazer isso, é importante que você faça a `Close` idêntica da implementação `Dispose` e considere implementar a `IDisposable.Dispose` método explicitamente.  
  
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
 Tipos finalizáveis são tipos que estendem o padrão básico de Dispose, substituindo o finalizador e fornecendo o caminho de código de finalização no `Dispose(bool)` método.  
  
 Os finalizadores são notoriamente difíceis de implementar corretamente, principalmente porque você não pode fazer algumas premissas (normalmente válidas) sobre o estado do sistema durante sua execução. As diretrizes a seguir devem ser levadas em consideração cuidadosa.  
  
 Observe que algumas das diretrizes se aplicam não apenas para o `Finalize` método, mas, para qualquer código chamado a partir de um finalizador. No caso de Dispose padrão básico definido anteriormente, isso significa que a lógica que é executado dentro de `Dispose(bool disposing)` quando o `disposing` parâmetro é falso.  
  
 Se a classe base já é finalizável e implementa o padrão básico de Dispose, você não deve substituir `Finalize` novamente. Apenas em vez disso, deve substituir o `Dispose(bool)` método para fornecer a lógica de limpeza de recursos adicionais.  
  
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
  
 Considere cuidadosamente qualquer caso em que você acha que um finalizador é necessária. Há um real custo associado a instâncias de finalizadores, do ponto de vista de complexidade de um desempenho e o código. Preferir usar wrappers de recursos, como <xref:System.Runtime.InteropServices.SafeHandle> para encapsular recursos não gerenciados, sempre que possível, caso em que um finalizador se torna desnecessário porque o wrapper é responsável por sua própria limpeza de recursos.  
  
 **X DO NOT** tornar os tipos de valor finalizáveis.  
  
 Somente os tipos de referência, na verdade, obterem finalizados pelo CLR, e, portanto, qualquer tentativa de colocar um finalizador em um tipo de valor será ignorada. Os compiladores c# e C++ impõem essa regra.  
  
 **✓ DO** fazer um tipo finalizáveis se o tipo é responsável pela liberação de um recurso não gerenciado que não tem seu próprio finalizador.  
  
 Ao implementar o finalizador, simplesmente chame `Dispose(false)` e coloque toda lógica de limpeza de recursos dentro de `Dispose(bool disposing)` método.  
  
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
  
 Isso oferece aos usuários do tipo de um meio para explicitamente executar limpeza determinística desses mesmos recursos para os quais o finalizador é responsável.  
  
 **X DO NOT** acessar quaisquer objetos finalizáveis no caminho de código do finalizador, porque não há risco significativo que eles serão já ter sido finalizados.  
  
 Por exemplo, um objeto finalizável um que tem uma referência a outro objeto finalizável B não é possível usar com confiança B do finalizador, ou vice-versa. Os finalizadores são chamados em ordem aleatória (sem uma garantia de ordenação fraca para finalização crítica).  
  
 Além disso, lembre-se de que os objetos armazenados em variáveis estáticas são coletados em determinados pontos durante um descarregamento de domínio de aplicativo ou ao sair do processo. Acessando uma variável estática que se refere a um objeto finalizável (ou chamar um método estático que pode usar os valores armazenados em variáveis estáticas) pode não ser seguro se <xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType> retorna true.  
  
 **✓ DO** fazer sua `Finalize` método protegido.  
  
 Os desenvolvedores de c#, C++ e VB.NET não precisa se preocupar com isso, porque os compiladores de ajudam a impor essa diretriz.  
  
 **X DO NOT** escape permitem exceções da lógica finalizador, exceto para falhas críticas do sistema.  
  
 Se uma exceção for gerada de um finalizador, o CLR será desligado a todo o processo (a partir do .NET Framework versão 2.0), impedindo que outros finalizadores executando e recursos do que está sendo lançada de uma maneira controlada.  
  
 **✓ CONSIDER** criando e usando um objeto finalizável crítico (um tipo com uma hierarquia de tipo que contém <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) para situações em que um finalizador absolutamente deve executar mesmo em caso de thread e os descarregamentos de domínio de aplicativo forçada será anulada.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Padrões comuns de Design](../../../docs/standard/design-guidelines/common-design-patterns.md)  
- [Coleta de lixo](../../../docs/standard/garbage-collection/index.md)
