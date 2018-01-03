---
title: "Noções básicas da segurança de acesso do código"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [.NET Framework], code access security
ms.assetid: 4eaa6535-d9fe-41a1-91d8-b437cfc16921
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fbeae8d01d9ef03c476679ea7fc59273b7a0a0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="code-access-security-basics"></a>Noções básicas da segurança de acesso do código
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Todos os aplicativos que tem como alvo o common language runtime (ou seja, todos os aplicativos gerenciados) devem interagir com o sistema de segurança do tempo de execução. Quando um aplicativo gerenciado é carregado, o seu host lhe concede automaticamente um conjunto de permissões. Essas permissões são determinadas pelas configurações de segurança local do host ou o aplicativo está em área restrita. Dependendo dessas permissões, o aplicativo é executado corretamente ou gera uma exceção de segurança.  
  
 O host padrão para aplicativos de desktop permite que o código executado em confiança total. Portanto, se seu aplicativo tem como alvo a área de trabalho, ele tem uma permissão irrestrita definido. Outros hosts ou as áreas restritas fornecem um conjunto de aplicativos de permissões limitado. Como o conjunto de permissões pode ser alterado de host para host, você deve projetar seu aplicativo para usar somente as permissões que permite que o host de destino.  
  
 Você deve estar familiarizado com os seguintes conceitos de segurança de acesso de código para escrever aplicativos efetivos que visam o common language runtime:  
  
-   **Código fortemente tipado**: código fortemente tipado é o código que acessa os tipos somente em modos bem definidos, permitidos. Por exemplo, dada uma referência de objeto válido, código fortemente tipado pode acessar memória em offsets fixos que correspondem aos membros do campo real. Se o código acessar a memória em offsets arbitrários fora do intervalo de memória que pertence a esse objeto publicamente exposto campos, não é fortemente tipado. Para habilitar o código para se beneficiar da segurança de acesso ao código, você deve usar um compilador que gera código fortemente tipado verificável. Para obter mais informações, consulte o [código de tipo seguro verificável gravação](#typesafe_code) seção mais adiante neste tópico.  
  
-   **Sintaxe imperativa e declarativa**: código que tem como alvo o common language runtime pode interagir com o sistema de segurança de solicitar permissões, exigindo que os chamadores têm permissões especificadas e substituir determinados (configurações de segurança receber privilégios suficientes). Usar duas formas de sintaxe para interagir programaticamente com o sistema de segurança do .NET Framework: sintaxe declarativa e sintaxe obrigatório. Chamadas declarativas são executadas usando atributos; chamadas de imperativas são executadas usando as novas instâncias de classes no seu código. Algumas chamadas podem ser executadas apenas imperativa, outras podem ser executadas apenas declarativamente e algumas chamadas podem ser executadas de qualquer maneira.  
  
-   **Proteger as bibliotecas de classe**: uma biblioteca de classes segura usa demandas de segurança para garantir que os chamadores da biblioteca tenham permissão para acessar os recursos que expõe a biblioteca. Por exemplo, uma biblioteca de classes segura pode ter um método para a criação de arquivos que seriam exigem que os chamadores tem permissões para criar arquivos. O .NET Framework consiste em bibliotecas de classes segura. Você deve estar ciente das permissões necessárias para acessar qualquer biblioteca que usa seu código. Para obter mais informações, consulte o [usando bibliotecas de classe Secure](#secure_library) seção mais adiante neste tópico.  
  
-   **Código transparente**: começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], além de identificar as permissões específicas, você também deve determinar se seu código deve ser executado como transparente de segurança. Código transparente de segurança não é possível chamar tipos ou membros que são identificados como críticas de segurança. Essa regra se aplica a aplicativos de confiança total, bem como aplicativos parcialmente confiáveis. Para obter mais informações, consulte [código transparente de segurança](../../../docs/framework/misc/security-transparent-code.md).  
  
<a name="typesafe_code"></a>   
## <a name="writing-verifiably-type-safe-code"></a>Escrevendo código fortemente tipado verificável  
 Compilação do Just-in-time (JIT) executa um processo de verificação que examina o código e tenta determinar se o código fortemente tipado. Código que é aprovado durante a verificação seja fortemente tipado é chamado *código fortemente tipado verificável*. Código pode ser fortemente tipado, ainda pode não ser fortemente tipado verificável devido às limitações do processo de verificação ou do compilador. Nem todos os idiomas são fortemente tipadas e alguns compiladores de linguagem, como o Microsoft Visual C++, não é possível gerar código gerenciado fortemente tipado verificável. Para determinar se o compilador de linguagem que você usar gera código fortemente tipado verificável, consulte a documentação do compilador. Se você usar um compilador de linguagem que gera código fortemente tipado verificável somente quando você evitar determinadas construções de linguagem, talvez você queira usar o [ferramenta PEVerify](../../../docs/framework/tools/peverify-exe-peverify-tool.md) para determinar se o seu código fortemente tipado verificável.  
  
 Código que não seja fortemente tipado verificável pode tentar executar se a política de segurança permite que o código ignorar a verificação. No entanto, como segurança de tipo é uma parte essencial do mecanismo de tempo de execução para assemblies com isolamento, segurança não pode ser confiável imposta se código viola as regras de segurança de tipos. Por padrão, código que não seja fortemente tipado é permitido para ser executado somente se for originado do computador local. Portanto, o código móvel deve ser fortemente tipado.  
  
<a name="secure_library"></a>   
## <a name="using-secure-class-libraries"></a>Usando bibliotecas de classes segura  
 Se seu código solicita e está concedidas as permissões exigidas para a biblioteca de classes, ele terá permissão para acessar a biblioteca e os recursos que expõe a biblioteca estará protegidos contra acesso não autorizado. Se seu código não tiver as permissões apropriadas, ele não ter permissão para acessar a biblioteca de classe e código mal-intencionado não poderá usar seu código indiretamente acessar recursos protegidos. Outro código que chama o código também deve ter permissão para acessar a biblioteca. Se não existir, seu código será restrita seja bem executado.  
  
 Segurança de acesso do código não elimina a possibilidade de erros humanos em escrever código. No entanto, se seu aplicativo usa bibliotecas de classe seguro para acessar recursos protegidos, o risco de segurança para o código do aplicativo é reduzido, porque as bibliotecas de classe são inspecionadas atentamente os problemas potenciais de segurança.  
  
## <a name="declarative-security"></a>Segurança declarativa  
 Sintaxe de segurança declarativa usa [atributos](../../../docs/standard/attributes/index.md) colocar informações de segurança para o [metadados](../../../docs/standard/metadata-and-self-describing-components.md) do seu código. Atributos podem ser colocados no nível de assembly, classe ou membro, para indicar o tipo de solicitação, demanda ou substituição que você deseja usar. As solicitações são usadas em aplicativos que o common language runtime para informar o sistema de segurança de tempo de execução sobre as permissões que seu aplicativo precisa ou não deseja como destino. Exigências e substituições são usadas em bibliotecas para ajudar a proteger os recursos de chamadores ou substituir o comportamento de segurança padrão.  
  
> [!NOTE]
>  No [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], houve alterações importantes para o modelo de segurança do .NET Framework e terminologia. Para obter mais informações sobre essas alterações, consulte [alterações de segurança](../../../docs/framework/security/security-changes.md).  
  
 Para usar a segurança declarativa chamadas, você deve inicializar os dados de estado do objeto de permissão para que ele representa a forma particular da permissão que você precisa. Cada permissão interna tem um atributo que é passado um <xref:System.Security.Permissions.SecurityAction> enumeração para descrever o tipo de operação de segurança você deseja executar. No entanto, as permissões também aceitam seus próprios parâmetros que são exclusivos a eles.  
  
 O fragmento de código a seguir mostra a sintaxe declarativa para solicitar que os chamadores do seu código tem uma permissão personalizada chamada `MyPermission`. Essa permissão é uma permissão personalizada hipotética e não existe no .NET Framework. Neste exemplo, a chamada declarativa é colocada diretamente antes da definição de classe, especificando que essa permissão seja aplicado ao nível de classe. O atributo é passado um **SecurityAction. Demand** para especificar que os chamadores devem ter essa permissão para executar.  
  
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
 Sintaxe de segurança imperativa emite uma chamada de segurança, criando uma nova instância do objeto de permissão que você deseja invocar. Você pode usar a sintaxe fundamental realizar demandas e substituições, mas não a solicitações.  
  
 Antes de fazer a segurança chamar, você deverá inicializar os dados de estado do objeto de permissão para que ele representa o formulário específico da permissão que é necessário. Por exemplo, ao criar um <xref:System.Security.Permissions.FileIOPermission> do objeto, você pode usar o construtor para inicializar o **FileIOPermission** para que ele represente qualquer acesso irrestrito a todos os arquivos ou nenhum acesso a arquivos do objeto. Ou, você pode usar outro **FileIOPermission** objeto, passando o objeto de parâmetros que indicam o tipo de acesso que você deseja para representar (ou seja, leitura, acrescentar ou gravação) e arquivos que você deseja que o objeto para proteger.  
  
 Além de usar a sintaxe de segurança imperativa para invocar um objeto de segurança, você pode usar para inicializar um grupo de permissões em um conjunto de permissões. Por exemplo, essa técnica é a única maneira de executar com confiança [assert](../../../docs/framework/misc/using-the-assert-method.md) chama em várias permissões em um método. Use o <xref:System.Security.PermissionSet> e <xref:System.Security.NamedPermissionSet> classes para criar um grupo de permissões e, em seguida, chame o método apropriado para invocar a chamada de segurança desejado.  
  
 Você pode usar a sintaxe fundamental realizar demandas e substituições, mas não a solicitações. Você pode usar a sintaxe fundamental para atender às demandas e substituições em vez da sintaxe declarativa quando informações necessárias para inicializar o estado de permissão se torna conhecidas somente em tempo de execução. Por exemplo, se você deseja garantir que os chamadores tem permissão para ler um determinado arquivo, mas você não souber o nome do arquivo até o tempo de execução, use uma demanda obrigatória. Você também pode optar por usar verificações imperativas em vez de verificações declarativas quando você precisa determinar em tempo de execução se mantém uma condição e, com base no resultado do teste, fazer uma exigência de segurança (ou não).  
  
 O fragmento de código a seguir mostra a sintaxe fundamental para solicitar que os chamadores do seu código tem uma permissão personalizada chamada `MyPermission`. Essa permissão é uma permissão personalizada hipotética e não existe no .NET Framework. Uma nova instância da `MyPermision` é criado no `MyMethod`, preservando apenas esse método com a chamada de segurança.  
  
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
 A maioria dos aplicativos e componentes (exceto bibliotecas seguras) não devem diretamente chamar código não gerenciado. Há vários motivos para isso. Se o código chama diretamente o código não gerenciado, ele não poderá ser executado em muitas circunstâncias, pois o código deve receber um alto nível de confiança para chamar código nativo. Se a política é modificada para permitir que esse aplicativo ser executado, ele pode reduzir significativamente a segurança do sistema, deixando o aplicativo pode executar quase qualquer operação.  
  
 Além disso, o código que tem permissão para acessar código não gerenciado provavelmente pode executar quase qualquer operação chamando uma API não gerenciada. Por exemplo, o código que tem permissão para chamar código não gerenciado não é necessário <xref:System.Security.Permissions.FileIOPermission> para acessar um arquivo; ele pode chamar apenas um arquivo (Win32) não gerenciado API diretamente, ignorando o arquivo gerenciado API que requer **FileIOPermission**. Se o código gerenciado tem permissão para chamar código não gerenciado e chamam diretamente no código não gerenciado, o sistema de segurança será possível impor com segurança as restrições de segurança, pois o tempo de execução não é possível impor essas restrições em código não gerenciado.  
  
 Se você deseja que seu aplicativo para executar uma operação que requer acesso a código não gerenciado, ele deve fazer isso por meio de uma classe gerenciada confiável que encapsula a funcionalidade necessária (se existir tal classe). Não crie uma classe wrapper por conta própria se já existir em uma biblioteca de classes segura. A classe de invólucro, o que deve ser concedida a um alto grau de confiança a ser permitidas para fazer a chamada para código não gerenciado, é responsável por exigindo que os chamadores tem as permissões apropriadas. Se você usar a classe de invólucro, o seu código precisa apenas solicitar e receber as permissões que exige a classe de invólucro.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.NamedPermissionSet>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Assert](../../../docs/framework/misc/using-the-assert-method.md)  
 [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md)  
 [Noções Básicas da Segurança de Acesso do Código](../../../docs/framework/misc/code-access-security-basics.md)  
 [Atributos](../../../docs/standard/attributes/index.md)  
 [Metadados e componentes autodescritivos](../../../docs/standard/metadata-and-self-describing-components.md)
