---
title: Noções básicas da segurança de acesso do código
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
ms.openlocfilehash: 08d708e8f98bd2fe06757df3033a512e2fe1f3c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400053"
---
# <a name="code-access-security-basics"></a>Noções básicas da segurança de acesso do código

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

Cada aplicativo que tenha como alvo o tempo de execução do idioma comum (ou seja, todos os aplicativos gerenciados) deve interagir com o sistema de segurança do tempo de execução. Quando um aplicativo gerenciado é carregado, seu host concede automaticamente um conjunto de permissões. Essas permissões são determinadas pelas configurações de segurança local do host ou pela caixa de areia em que o aplicativo está. Dependendo dessas permissões, o aplicativo ou é executado corretamente ou gera uma exceção de segurança.

O host padrão para aplicativos de desktop permite que o código seja executado em total confiança. Portanto, se o aplicativo tiver como alvo a área de trabalho, ele tem um conjunto de permissões irrestrito. Outros hosts ou caixas de areia fornecem um conjunto de permissões limitada para aplicativos. Como o conjunto de permissões pode mudar de host para host, você deve projetar seu aplicativo para usar apenas as permissões que o host de destino permite.

Você deve estar familiarizado com os seguintes conceitos de segurança de acesso a código, a fim de escrever aplicativos eficazes que visam o tempo de execução do idioma comum:

- **Código seguro de tipo :** Código de segurança de tipo é um código que acessa os tipos apenas de maneiras bem definidas e permitidas. Por exemplo, dada uma referência de objeto válida, o código de segurança de tipo pode acessar a memória em deslocamentos fixos que correspondem a membros de campo reais. Se o código acessar a memória em deslocamentos arbitrários fora do alcance da memória que pertence aos campos expostos publicamente desse objeto, ele não é seguro para o tipo. Para permitir que o código se beneficie da segurança de acesso ao código, você deve usar um compilador que gere código seguro de tipo verificável. Para obter mais informações, consulte a [seção Código de segurança de tipo](#typesafe_code) de escrita mais tarde neste tópico.

- **Sintaxe imperativa e declarativa**: O código que visa o tempo de execução do idioma comum pode interagir com o sistema de segurança solicitando permissões, exigindo que os chamadores tenham permissões especificadas e substituindo certas configurações de segurança (dado privilégios suficientes). Você usa duas formas de sintaxe para interagir programáticamente com o sistema de segurança .NET Framework: sintaxe declarativa e sintaxe imperativa. As chamadas declarativas são realizadas por meio de atributos; chamadas imperativas são realizadas usando novas instâncias de classes dentro do seu código. Algumas chamadas podem ser realizadas apenas de forma impermeável, outras podem ser realizadas apenas declarativamente, e algumas chamadas podem ser realizadas de qualquer maneira.

- **Bibliotecas de classe seguras**: Uma biblioteca de classe segura usa as exigências de segurança para garantir que os chamadores da biblioteca tenham permissão para acessar os recursos que a biblioteca expõe. Por exemplo, uma biblioteca de classe segura pode ter um método para criar arquivos que exigiriam que seus chamadores tivessem permissões para criar arquivos. O .NET Framework consiste em bibliotecas de classe seguras. Você deve estar ciente das permissões necessárias para acessar qualquer biblioteca que seu código use. Para obter mais informações, consulte a [seção Usar bibliotecas de classe seguras](#secure_library) mais tarde neste tópico.

- **Código transparente**: A partir do .NET Framework 4, além de identificar permissões específicas, você também deve determinar se seu código deve ser executado como transparente à segurança. O código transparente de segurança não pode chamar tipos ou membros identificados como críticos de segurança. Essa regra se aplica a aplicativos de confiança total, bem como a aplicativos parcialmente confiáveis. Para obter mais informações, consulte [Código transparente de segurança](security-transparent-code.md).

<a name="typesafe_code"></a>

## <a name="writing-verifiably-type-safe-code"></a>Escrevendo um código fortemente tipado verificável

A compilação Just-in-time (JIT) realiza um processo de verificação que examina o código e tenta determinar se o código é seguro para o tipo. O código comprovado durante a verificação para ser seguro por tipo é chamado *de código seguro de tipo*. O código pode ser seguro para o tipo, mas pode não ser verificável mente seguro devido às limitações do processo de verificação ou do compilador. Nem todos os idiomas são seguros para o tipo, e alguns compiladores de idiomas, como o Microsoft Visual C++, não podem gerar código gerenciado seguro por tipo. Para determinar se o compilador de idiomas que você usa gera código seguro de tipo, consulte a documentação do compilador. Se você usar um compilador de idiomas que gere código seguro apenas para tipos quando evitar determinadas construções de idioma, você pode querer usar a [ferramenta PEVerify](../tools/peverify-exe-peverify-tool.md) para determinar se seu código é verificávelmente seguro para o tipo.

Um código que não seja verificável mente seguro para o tipo pode tentar executar se a política de segurança permitir que o código contorne a verificação. No entanto, como a segurança do tipo é uma parte essencial do mecanismo de isolamento dos conjuntos, a segurança não pode ser aplicada de forma confiável se o código violar as regras de segurança do tipo. Por padrão, o código que não é seguro para o tipo só pode ser executado se ele se originar do computador local. Portanto, o código móvel deve ser um tipo seguro.

<a name="secure_library"></a>

## <a name="using-secure-class-libraries"></a>Usando bibliotecas de classe seguras

Se o seu código solicitar e receber as permissões exigidas pela biblioteca de classes, será permitido acessar a biblioteca e os recursos que a biblioteca expõe serão protegidos contra acesso não autorizado. Se o seu código não tiver as permissões apropriadas, ele não poderá acessar a biblioteca de classes, e o código malicioso não poderá usar seu código para acessar indiretamente recursos protegidos. Outro código que chama seu código também deve ter permissão para acessar a biblioteca. Se isso não acontecer, seu código também será impedido de funcionar.

A segurança de acesso ao código não elimina a possibilidade de erro humano na escrita do código. No entanto, se seu aplicativo usar bibliotecas de classe seguras para acessar recursos protegidos, o risco de segurança para o código do aplicativo é diminuído, porque as bibliotecas de classe são examinadas de perto por possíveis problemas de segurança.

## <a name="declarative-security"></a>Segurança declarativa

A sintaxe declarativa de segurança usa [atributos](../../standard/attributes/index.md) para colocar informações de segurança nos [metadados](../../standard/metadata-and-self-describing-components.md) do seu código. Os atributos podem ser colocados no nível de montagem, classe ou membro, para indicar o tipo de solicitação, demanda ou substituição que você deseja usar. As solicitações são usadas em aplicativos que visam o tempo de execução do idioma comum para informar o sistema de segurança em tempo de execução sobre as permissões que seu aplicativo precisa ou não deseja. Demandas e substituições são usadas em bibliotecas para ajudar a proteger os recursos dos chamadores ou para substituir o comportamento de segurança padrão.

> [!NOTE]
> No Quadro .NET 4, houve mudanças importantes no modelo de segurança e terminologia do Quadro .NET. Para obter mais informações sobre essas alterações, consulte [Alterações de segurança](../security/security-changes.md).

Para usar chamadas de segurança declarativas, você deve inicializar os dados do estado do objeto de permissão para que ele represente a forma específica de permissão que você precisa. Cada permissão incorporada tem um atributo que é passado uma <xref:System.Security.Permissions.SecurityAction> enumeração para descrever o tipo de operação de segurança que você deseja executar. No entanto, as permissões também aceitam seus próprios parâmetros que são exclusivos para eles.

O fragmento de código a seguir mostra sintaxe declarativa para solicitar `MyPermission`que os chamadores do seu código tenham uma permissão personalizada chamada . Essa permissão é uma permissão personalizada hipotética e não existe no Quadro .NET. Neste exemplo, a chamada declarativa é colocada diretamente antes da definição da classe, especificando que essa permissão seja aplicada ao nível de classe. O atributo é aprovado em uma estrutura **SecurityAction.Demand** para especificar que os chamadores devem ter essa permissão para serem executados.

```vb
<MyPermission(SecurityAction.Demand, Unrestricted = True)> Public Class MyClass1

   Public Sub New()
      'The constructor is protected by the security call.
   End Sub

   Public Sub MyMethod()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'This method is protected by the security call.
   End Sub
End Class
```

```csharp
[MyPermission(SecurityAction.Demand, Unrestricted = true)]
public class MyClass
{
   public MyClass()
   {
      //The constructor is protected by the security call.
   }

   public void MyMethod()
   {
      //This method is protected by the security call.
   }

   public void YourMethod()
   {
      //This method is protected by the security call.
   }
}
```

## <a name="imperative-security"></a>Segurança obrigatória

A sintaxe de segurança imperativa emite uma chamada de segurança criando uma nova instância do objeto de permissão que você deseja invocar. Você pode usar a sintaxe imperativa para realizar demandas e substituições, mas não solicitações.

Antes de fazer a chamada de segurança, você deve inicializar os dados do estado do objeto de permissão para que ele represente a forma particular da permissão que você precisa. Por exemplo, ao <xref:System.Security.Permissions.FileIOPermission> criar um objeto, você pode usar o construtor para inicializar o objeto **FileIOPermission** para que ele represente acesso irrestrito a todos os arquivos ou sem acesso a arquivos. Ou, você pode usar um objeto **FileIOPermission** diferente, passando parâmetros que indicam o tipo de acesso que você deseja que o objeto represente (isto é, ler, anexar ou gravar) e quais arquivos você deseja que o objeto proteja.

Além de usar a sintaxe de segurança imperativa para invocar um único objeto de segurança, você pode usá-lo para inicializar um grupo de permissões em um conjunto de permissões. Por exemplo, essa técnica é a única maneira de executar de forma confiável [chamadas de afirmação](using-the-assert-method.md) em várias permissões em um método. Use <xref:System.Security.PermissionSet> as <xref:System.Security.NamedPermissionSet> classes e para criar um grupo de permissões e, em seguida, chame o método apropriado para invocar a chamada de segurança desejada.

Você pode usar a sintaxe imperativa para realizar demandas e substituições, mas não solicitações. Você pode usar sintaxe imperativa para demandas e substituições em vez de sintaxe declarativa quando as informações que você precisa para inicializar o estado de permissão se tornam conhecidos apenas no tempo de execução. Por exemplo, se você quiser garantir que os chamadores tenham permissão para ler um determinado arquivo, mas você não sabe o nome desse arquivo até o tempo de execução, use uma demanda imperativa. Você também pode optar por usar verificações imperativas em vez de verificações declarativas quando precisar determinar no tempo de execução se uma condição se mantém e, com base no resultado do teste, fazer uma exigência de segurança (ou não).

O fragmento de código a seguir mostra sintaxe imperativa para `MyPermission`solicitar que os chamadores do seu código tenham uma permissão personalizada chamada . Essa permissão é uma permissão personalizada hipotética e não existe no Quadro .NET. Uma nova `MyPermission` instância de `MyMethod`é criada em, protegendo apenas este método com a chamada de segurança.

```vb
Public Class MyClass1

   Public Sub New()

   End Sub

   Public Sub MyMethod()
      'MyPermission is demanded using imperative syntax.
      Dim Perm As New MyPermission()
      Perm.Demand()
      'This method is protected by the security call.
   End Sub

   Public Sub YourMethod()
      'YourMethod 'This method is not protected by the security call.
   End Sub
End Class
```

```csharp
public class MyClass {
   public MyClass(){

   }

   public void MyMethod() {
       //MyPermission is demanded using imperative syntax.
       MyPermission Perm = new MyPermission();
       Perm.Demand();
       //This method is protected by the security call.
   }

   public void YourMethod() {
       //This method is not protected by the security call.
   }
}
```

## <a name="using-managed-wrapper-classes"></a>Usando classes de wrapper gerenciadas

A maioria dos aplicativos e componentes (exceto bibliotecas seguras) não deve chamar diretamente código não gerenciado. Há várias razões para isso. Se o código chamar código não gerenciado diretamente, ele não será permitido ser executado em muitas circunstâncias, porque o código deve ser concedido um alto nível de confiança para chamar código nativo. Se a política for modificada para permitir que tal aplicativo seja executado, ele pode enfraquecer significativamente a segurança do sistema, deixando o aplicativo livre para realizar quase qualquer operação.

Além disso, o código que tem permissão para acessar código não gerenciado provavelmente pode realizar quase qualquer operação, chamando-a para uma API não gerenciada. Por exemplo, o código que tem permissão <xref:System.Security.Permissions.FileIOPermission> para chamar código não gerenciado não precisa acessar um arquivo; ele pode simplesmente chamar uma API de arquivo não gerenciado (Win32) diretamente, ignorando a API de arquivo gerenciado que requer **FileIOPermission**. Se o código gerenciado tiver permissão para chamar em código não gerenciado e chamar diretamente para código não gerenciado, o sistema de segurança não será capaz de impor restrições de segurança de forma confiável, uma vez que o tempo de execução não pode impor tais restrições em código não gerenciado.

Se você quiser que seu aplicativo execute uma operação que requer acesso a código não gerenciado, ele deve fazê-lo através de uma classe gerenciada confiável que envolve a funcionalidade necessária (se tal classe existir). Não crie uma classe de invólucro se já existir em uma biblioteca de classes segura. A classe de invólucro, que deve ser concedida um alto grau de confiança para ser permitida a fazer a chamada em código não gerenciado, é responsável por exigir que seus chamadores tenham as permissões apropriadas. Se você usar a classe de invólucro, seu código só precisa solicitar e receber as permissões que a classe de invólucro exige.

## <a name="see-also"></a>Confira também

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.NamedPermissionSet>
- <xref:System.Security.Permissions.SecurityAction>
- [Assert](using-the-assert-method.md)
- [Segurança de acesso a código](code-access-security.md)
- [Noções básicas da segurança de acesso do código](code-access-security-basics.md)
- [Atributos](../../standard/attributes/index.md)
- [Metadados e componentes autodescritivos](../../standard/metadata-and-self-describing-components.md)
