# Teste METRICS E COVERAGE

Este teste ocorre a validadção por meio da % do código-fonte que é abrangida pelos testes, proporcionando uma medida crucial conhecida como cobertura de código. Essa métrica desempenha um papel fundamental ao identificar áreas não testadas, permitindo uma avaliação mais precisa da eficácia dos testes aplicados. No contexto específico deste teste, a meta de cobertura estabelecida é de 30% para as classes, o que significa que a cobertura deverá ser sobre as classes nas quais os testes devem ser exercidos.

 ![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/0f2c92ed-0d29-4718-8bcf-5364c95e06e8)

## View

Os resultados dos testes são satisfatorios, demonstrando que as classes AppView, Perfil e Serviço estão operando de acordo com as expectativas. Os métodos demonstraram uma manipulação precisa das entradas simuladas dos testes realizados. A execução bem-sucedida dos testes JUnit para essas classes valida de forma eficaz a funcionalidade geral da aplicação.


```
 }
    
   
    @Test
    public void testMenuInicial() throws Exception {
        System.out.println("menuInicial");
        String input = "1";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        AppView instance = new AppView();
        instance.menuInicial();
        
    }

    /**
     * Test of mostraMsgInvalida method, of class AppView.
     */
    @Test
    public void testMostraMsgInvalida() {
        System.out.println("mostraMsgInvalida");
        AppView.mostraMsgInvalida();
        
    }

    
    @Test
    public void testMensagemAlertaCadastro() {
        System.out.println("mensagemAlertaCadastro");
        int expResult =1;
        String input = "1";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        int result = AppView.mensagemAlertaCadastro();
        assertEquals(expResult, result);
        
    }


    @Test
    public void testNaoProcederCadastro() {
        System.out.println("naoProcederCadastro");
        AppView.naoProcederCadastro();
       
    }
    
```


 ![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/95590b9f-440b-4337-82e3-aff02d9cbe88)


## Teste de Conexão – dbConnection

Inicialmente, o teste enfrentou um problema de configuração, uma vez que estava comparando `` Connection expResult = null; com Connection result = instance.getConnection(); usando assertEquals(expResult, result);``. Isso resultou em falhas, a menos que ``instance.getConnection() também retornasse null``. Para garantir o sucesso da conexão, foi necessário realizar a comparação utilizando assertNotEquals ou assertNotNull. Esta correção visa evitar falsos positivos e assegurar que a validação da conexão seja realizada de maneira adequada, contribuindo para a confiabilidade do teste e a precisão na detecção de falhas na conexão do banco de dados.

```
   
    @Test
    public void testGetConnection() throws Exception {
    System.out.println("getConnection");
    DbConnection instance = new DbConnection();
    Connection result = instance.getConnection();
    assertNotNull(result);
}

```

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/6b27a1c4-4c70-4bdc-8246-0726669a487d)


## Perfil – dbPerfil

O sistema oferece as funcionalidades para cadastrar, visualizar, atualizar e excluir perfis, armazenando as informações de forma segura no nosso banco de dado MySQL "trocaservico". São implementados testes automatizados com o objetivo de assegurar o correto funcionamento das operações de salvar, buscar, atualizar e excluir perfis, contribuindo assim para a robustez e confiabilidade do sistema


```
 /**
     
    @Test
    public void testSalvarBuscarAtualizarDeletarPerfil() throws Exception {
        System.out.println("testSalvarBuscarAtualizarDeletarPerfil");

        // Testar o método salvarCadastro
        Perfil perfilCadastro = new Perfil("Teste", 30, "teste@gmail.com", "12345678901", "Descrição Teste", "Cidade Teste", "Bairro Teste", "Interesse1, Interesse2", "5", "foto_teste.jpg", "Habilidade1, Habilidade2");
        DbPerfil dbPerfil = new DbPerfil();
        dbPerfil.salvarCadastro(perfilCadastro);

        // Testar o método buscarPerfil
        String cpf = "12345678901";
        Perfil perfilBuscado = dbPerfil.buscarPerfil(cpf);
        assertNotNull(perfilBuscado);
        assertEquals(perfilCadastro.getNome(), perfilBuscado.getNome());
        assertEquals(perfilCadastro.getIdade(), perfilBuscado.getIdade());
        assertEquals(perfilCadastro.getEmail(), perfilBuscado.getEmail());
        assertEquals(perfilCadastro.getCpf(), perfilBuscado.getCpf());
        assertEquals(perfilCadastro.getDescSer(), perfilBuscado.getDescSer());
        assertEquals(perfilCadastro.getCidade(), perfilBuscado.getCidade());
        assertEquals(perfilCadastro.getBairro(), perfilBuscado.getBairro());
        assertEquals(perfilCadastro.getAreasInteresse(), perfilBuscado.getAreasInteresse());
        assertEquals(perfilCadastro.getTempoEx(), perfilBuscado.getTempoEx());
        assertEquals(perfilCadastro.getFtPerfil(), perfilBuscado.getFtPerfil());
        assertEquals(perfilCadastro.getHabilidades(), perfilBuscado.getHabilidades());

        // Testar o método atualizarPerfil
        String novoNome = "Novo Nome";
        String campoAtualizacao = "nome";
        String mensagemAtualizar = dbPerfil.atualizarPerfil(cpf, campoAtualizacao, novoNome);
        assertEquals("Atualização realizada com sucesso!", mensagemAtualizar);

        // Verificar se o perfil foi atualizado corretamente
        perfilBuscado = dbPerfil.buscarPerfil(cpf);
        assertNotNull(perfilBuscado);
        assertEquals(novoNome, perfilBuscado.getNome());

        // Testar o método deletarPerfil
        String mensagemDeletar = dbPerfil.deletarPerfil(cpf);
        assertEquals("Exclusão realizada com sucesso!", mensagemDeletar);

        // Verificar se o perfil foi removido corretamente
        perfilBuscado = dbPerfil.buscarPerfil(cpf);
        assertNull(perfilBuscado);
    }   

```

## Servico – dbServico

Os testes realizados para a classe foram bem-sucedidos, apontando para uma implementação precisa da conexão com o banco de dados e das operações CRUD. As classe são capazes de interagir de maneira eficaz com o banco de dados, garantindo o salvamento e recuperação adequados das informações relacionadas aos serviços. 

```
   @Test
    public void testSalvarCadastro() throws Exception {
        System.out.println("salvarCadastro");
        Servico cadastro = new Servico("AreaTeste", "DescTeste", "CidadeTeste", "BairroTeste", "TempoTeste", "12345678901");
        DbServico instance = new DbServico();
        instance.salvarCadastro(cadastro);

        // Adicione asserções conforme necessário para verificar o resultado do método
        // Por exemplo, você pode buscar o serviço do banco de dados e verificar se os dados correspondem
        List<Servico> result = instance.buscarServicos("AreaTeste");
        assertNotNull(result);
        assertFalse(result.isEmpty());
        assertEquals("AreaTeste", result.get(0).getArea());
        assertEquals("DescTeste", result.get(0).getDescSer());
        assertEquals("CidadeTeste", result.get(0).getCidade());
        assertEquals("BairroTeste", result.get(0).getBairro());
        assertEquals("TempoTeste", result.get(0).getTempoEx());
        assertEquals("12345678901", result.get(0).getCpf());
    }

   
    @Test
    public void testBuscarServicos() throws Exception {
        System.out.println("buscarServicos");
        String areasel = "AreaTeste";  // Área que você espera encontrar
        DbServico instance = new DbServico();

        // Adicione alguns dados ao banco de dados para teste
        Servico cadastro = new Servico(areasel, "DescTeste", "CidadeTeste", "BairroTeste", "TempoTeste", "12345678901");
        instance.salvarCadastro(cadastro);

        List<Servico> result = instance.buscarServicos(areasel);

        // Adicione asserções conforme necessário para verificar o resultado do método
        assertNotNull(result);
        assertFalse(result.isEmpty());
        assertEquals(areasel, result.get(0).getArea());
        assertEquals("DescTeste", result.get(0).getDescSer());
        assertEquals("CidadeTeste", result.get(0).getCidade());
        assertEquals("BairroTeste", result.get(0).getBairro());
        assertEquals("TempoTeste", result.get(0).getTempoEx());
        assertEquals("12345678901", result.get(0).getCpf());
    }

```

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/5cdba81b-4f02-4b3a-bfe1-77bad0c413a0)

## Controller

Os testes realizados para as classes Controller, PerfilController e ServicoController foram concluídos com sucesso, evidenciando que as operações desses controladores estão alinhadas com as expectativas estabelecidas.

```
   
    @Test
    public void testMenu() throws Exception {
        System.out.println("menu");
        int escolha = 0;
        Controller instance = new Controller();
        instance.menu(escolha);

    }

    @Test
    public void testAvaliarPerfis() {
        System.out.println("avaliarPerfis");
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        Controller instance = new Controller();
        instance.avaliarPerfis();

    }

    
    @Test
    public void testSair() {
        System.out.println("sair");
        Controller instance = new Controller();
        instance.sair();

    }

   
    @Test
    public void testDeletarServico() {
        System.out.println("deletarServico");
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        Controller instance = new Controller();
        instance.deletarServico();

    }

   
    @Test
    public void testAtualizarServico() {
        System.out.println("atualizarServico");
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        Controller instance = new Controller();
        instance.atualizarServico();

    }

    
    @Test
    public void testPublicarServico() {
        System.out.println("publicarServico");
        Controller instance = new Controller();
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        instance.publicarServico();

    }

   
    @Test
    public void testPesquisarServico() {
        System.out.println("pesquisarServico");
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        Controller instance = new Controller();
        instance.pesquisarServico();

    }

   
     @Test
    public void testCadastrarPerfil() {
        System.out.println("cadastrarPerfil");

        // Configura uma entrada simulada para o método cadastrarPerfil
        String input = "Nome do Perfil\n22\nperfil@teste.com\n12345678998\nteste descr\nteste cidade\nteste bairro\nareas de interesse\ntempo ex\nft perfil\nhabilidades";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);

        Controller instance = new Controller();
        instance.cadastrarPerfil();
    }

   
    @Test
    public void testVisualizarPerfil() {
        System.out.println("visualizarPerfil");
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        Controller instance = new Controller();
        instance.visualizarPerfil();
    }

    
    @Test
    public void testAtualizarPerfil() {
        System.out.println("atualizarPerfil");
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        Controller instance = new Controller();
        instance.atualizarPerfil();
    }

   
    @Test
    public void testDeletarPerfil() {
        System.out.println("deletarPerfil");
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        Controller instance = new Controller();
        instance.deletarPerfil();
    }
}

```
## PerfilController
```
   
  @Test
    public void testCadastrar() throws Exception {
        System.out.println("cadastrar");

        // Criar uma instância de Perfil para passar como argumento
        Perfil cadastro = new Perfil("Nome", 25, "email@teste.com", "12345678901",
                "Descrição", "Cidade", "Bairro", "Interesse1, Interesse2",
                "2", "foto.img", "Habilidade1, Habilidade2");

        PerfilController instance = new PerfilController();
        instance.cadastrar(cadastro);

    }


   
    @Test
    public void testAtualizar() throws Exception {
        System.out.println("atualizar");
        int opcao = 3;
        String cpf = "12345678901";
        String input = "12345678998";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        PerfilController instance = new PerfilController();
        instance.atualizar(opcao, cpf);
    }

  
    @Test
    public void testDeletar() throws Exception {
        System.out.println("deletar");
        String cpf = "12345678901";
        PerfilController instance = new PerfilController();
        instance.deletar(cpf);

    }

```
## ServicoController
```
   
 @Test
    public void testCadastrar() throws Exception {
        System.out.println("cadastrar");
        Servico cadastro = new Servico("Área", "Descrição", "Cidade", "Bairro", "Tempo", "CPF");
        ServicoController instance = new ServicoController();
        instance.cadastrar(cadastro);
    }

    
    @Test
    public void testVisualizar() throws Exception {
        System.out.println("testVisualizar");

        // Dados de exemplo para inserir no banco de dados de teste
        Servico cadastro1 = new Servico("Área1", "Descrição1", "Cidade1", "Bairro1", "Tempo1", "CPF1");
        Servico cadastro2 = new Servico("Área1", "Descrição2", "Cidade2", "Bairro2", "Tempo2", "CPF2");

        // Cadastrar os dados de exemplo no banco de dados de teste
        ServicoController controller = new ServicoController();
        controller.cadastrar(cadastro1);
        controller.cadastrar(cadastro2);

        // Redefinir a saída padrão para capturar a saída do método visualizar
        System.setOut(new PrintStream(outContent));

        // Testar o método visualizar com a área correta
        String area = "Área1";
        controller.visualizar(area);

    }

    
    @Test
    public void testDeletar() throws Exception {
        System.out.println("testDeletar");

        // Dados de exemplo para inserir no banco de dados de teste
        Servico cadastro = new Servico("Área", "Descrição", "Cidade", "Bairro", "Tempo", "CPF");
        ServicoController controller = new ServicoController();
        controller.cadastrar(cadastro);

        // Simular a entrada do usuário para o teste de deletar
        System.setIn(new ByteArrayInputStream("ID_DO_SERVICO\n".getBytes()));

        // Testar o método deletar
        controller.deletar("CPF");

        // Restaurar a entrada padrão
        System.setIn(System.in);
    }

    
    @Test
    public void testAtualizar() throws Exception {
        System.out.println("testAtualizar");

        // Dados de exemplo para inserir no banco de dados de teste
        Servico cadastro = new Servico("Área", "Descrição", "Cidade", "Bairro", "Tempo", "CPF");
        ServicoController controller = new ServicoController();
        controller.cadastrar(cadastro);

        // Simular a entrada do usuário para o teste de atualizar
        System.setIn(new ByteArrayInputStream("ID_DO_SERVICO\nNOVA_ATUALIZACAO\n".getBytes()));

        // Testar o método atualizar
        controller.atualizar(1, "CPF");

        // Restaurar a entrada padrão
        System.setIn(System.in);
    }

```


![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/d6e97700-3ad3-4684-b3f5-b5f23d223c78)


## Model

Os testes foram concluídos com êxito, sinalizando que a implementação das classes Perfil e Serviço está correta, oferecendo os métodos de acesso esperados para seus atributos. A implementação demonstra robustez, proporcionando uma estrutura adequada para representar perfis no contexto do aplicativo de troca de serviços. É digno de nota que a cobertura alcançada foi de 59% e 100%, indicando uma abrangência significativa nos testes realizados, o que contribui para a confiança na funcionalidade e integridade das classes.

```
   
 @Before
    public void setUp() {
        // Inicialize a instância antes de cada teste
        instance = new Perfil("Joao Marques", 22, "joao.marques@gmail.com", "74185296374",
                "Cozinheiro", "Contagem", "Linda Vista", "Moda", "2 anos", "foto.img", "Pratos saborosos");
    }
    @After
    public void tearDown() {
    }

    
     @Test
    public void testGetCpf() {
        System.out.println("getCpf");
        String expResult = "12345678901";
        instance.setCpf(expResult);
        String result = instance.getCpf();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetDescSer() {
        System.out.println("getDescSer");
        String expResult = "Descrição de teste";
        instance.setDescSer(expResult);
        String result = instance.getDescSer();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetCidade() {
        System.out.println("getCidade");
        String expResult = "Cidade Teste";
        instance.setCidade(expResult);
        String result = instance.getCidade();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetAreasInteresse() {
        System.out.println("getAreasInteresse");
        String expResult = "Interesse1, Interesse2";
        instance.setAreasInteresse(expResult);
        String result = instance.getAreasInteresse();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetBairro() {
        System.out.println("getBairro");
        String expResult = "Bairro Teste";
        instance.setBairro(expResult);
        String result = instance.getBairro();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetTempoEx() {
        System.out.println("getTempoEx");
        String expResult = "Experiência Teste";
        instance.setTempoEx(expResult);
        String result = instance.getTempoEx();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetFtPerfil() {
        System.out.println("getFtPerfil");
        String expResult = "foto_teste.jpg";
        instance.setFtPerfil(expResult);
        String result = instance.getFtPerfil();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetHabilidades() {
        System.out.println("getHabilidades");
        String expResult = "Habilidade1, Habilidade2";
        instance.setHabilidades(expResult);
        String result = instance.getHabilidades();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetNome() {
        System.out.println("getNome");
        String expResult = "Nome Teste";
        instance.setNome(expResult);
        String result = instance.getNome();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetIdade() {
        System.out.println("getIdade");
        int expResult = 30;
        instance.setIdade(expResult);
        int result = instance.getIdade();
        assertEquals(expResult, result);
    }

    @Test
    public void testGetEmail() {
        System.out.println("getEmail");
        String expResult = "teste@gmail.com";
        instance.setEmail(expResult);
        String result = instance.getEmail();
        assertEquals(expResult, result);
    }
    

```

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/cc42daf6-5b48-4c55-b034-24d1fcf0aa94)

 
## Troca de Serviços
Estes testes foram bem- sucedidos, no qual o  Sistema de Troca de Serviços, realizado entre um usuário e outro chegando numa cobertura de 70% do código;

```
  @Test
    public void testMenuInicial() throws Exception {
        System.out.println("menuInicial");
        String input = "1";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        AppView instance = new AppView();
        instance.menuInicial();
        
    }

   
    @Test
    public void testMostraMsgInvalida() {
        System.out.println("mostraMsgInvalida");
        AppView.mostraMsgInvalida();
        
    }

  
    @Test
    public void testMensagemAlertaCadastro() {
        System.out.println("mensagemAlertaCadastro");
        int expResult =1;
        String input = "1";
        InputStream in = new ByteArrayInputStream(input.getBytes());
        System.setIn(in);
        int result = AppView.mensagemAlertaCadastro();
        assertEquals(expResult, result);
        
    }

   
    @Test
    public void testNaoProcederCadastro() {
        System.out.println("naoProcederCadastro");
        AppView.naoProcederCadastro();
       
    }

```

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/7a5b39fd-6ea0-483d-90bb-75e081409535)


# Teste METRICS

Teste de Metrics Concluído com Sucesso. O teste de Metrics foi executado com êxito no código do Sistema de Troca de Serviços, e nenhuma falha foi identificada durante a análise. Todos os aspectos avaliados apresentaram resultados conforme esperado, validando assim a integridade e a eficácia do sistema. Este resultado positivo reforça a confiança na qualidade e no desempenho do código do Sistema de Troca de Serviços.

![image](https://github.com/Troca-Servico/Entrega-4-Metric-Coverage/assets/111398446/e9e1dc14-5b8e-4df3-a601-15865a2d228c)
