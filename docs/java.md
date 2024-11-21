#**Códigos em Java**

☕
---

###Menu de Palavras

~~~java
import java.util.Scanner;

public class exercicio104 {

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int opcao = 0;

        while (opcao != 12) {
            System.out.printf("""
ESCOLHA UMA DAS SEGUINTES OPÇÕES
1. Lê dez palavras e mostra a menor delas
2. Lê uma palavra e depois armazena a letra W em todas as posições pares da palavra
3. Lê uma frase e exibe o número de palavras existentes na frase
4. Lê uma palavra e retorna quantas vogais existem
5. Lê uma frase e mostra o seu tamanho
6. Lê uma palavra e mostra ela invertida (Por ex: amor - roma)
7. Lê 3 nomes e mostra o maior
8. Lê uma frase e substitui todas as vogais por X e mostra
9. Lê uma frase e retorna o número de vogais, de consoantes
10. Lê uma palavra e retorna indicando se é palíndroma (Por ex: arara é uma palavra palíndroma)
11. Lê uma frase e criptografa da seguinte maneira: A - X, E - Y, I - W, O - K, U - Z
12. Sair do Programa
ESCOLHA A OPÇÃO:
            """);
            opcao = scan.nextInt();
            scan.nextLine(); 
            switch (opcao) {
                case 1: // Lê dez palavras e mostra a menor delas
                scan.nextLine();
                    System.out.println("Escreva dez palavras:");
                    String menor_pal = scan.nextLine();
                    for (int i = 1; i < 10; i++) {
                        String palavra = scan.nextLine();
                        if (palavra.length() < menor_pal.length()) {
                            menor_pal = palavra;
                        }
                    }
                    System.out.println("A menor palavra é: " + menor_pal);
                    break;

                case 2: // Lê uma palavra e substitui W nas posições pares
                scan.nextLine();
                    System.out.println("Digite uma palavra:");
                    String palavra = scan.nextLine();
                    char[] caracteres = palavra.toCharArray(); 
                    for (int i = 1; i < caracteres.length; i += 2) { 
                        caracteres[i] = 'W'; 
                    }
                    String modificada = new String(caracteres); 
                    System.out.println("Palavra modificada: " + modificada);
                    break;

                case 3:
                    scan.nextLine();
                    System.out.println("Digite uma frase:");
                    String frase = scan.nextLine();
            
                    if (frase.isEmpty()) {
                        System.out.println("Número de palavras: 0");
                    } 
                    else {
                        String[] palavras = frase.split("\\s+");
                        System.out.println("Número de palavras: " + palavras.length);
                    }
                    break;

                case 4: // Conta o número de vogais em uma palavra
                    System.out.println("Digite uma palavra:");
                    String word = scan.nextLine();
                    int vogais = 0;
                    for (int i = 0; i < word.length(); i++) {
                        if ("aeiouAEIOU".indexOf(word.charAt(i)) != -1) {
                            vogais++;
                        }
                    }
                    System.out.println("Número de vogais: " + vogais);
                    break;

                case 5: // Mostra o tamanho de uma frase
                    System.out.println("Digite uma frase:");
                    String f = scan.nextLine();
                    System.out.println("Tamanho da frase: " + f.length());
                    break;

                case 6: // Inverte uma palavra
                    System.out.println("Digite uma palavra:");
                    String escrever = scan.nextLine();
                    String invertida = ""; 
                    for (int i = escrever.length() - 1; i >= 0; i--) { 
                        invertida += escrever.charAt(i); 
                    }
                    System.out.println("Palavra invertida: " + invertida);
                    break;



                case 7: // Lê 3 nomes e mostra o maior
                    System.out.println("Digite três nomes:");
                    String maior = "";
                    for (int i = 0; i < 3; i++) {
                        String nome = scan.nextLine();
                        if (nome.length() > maior.length()) {
                            maior = nome;
                        }
                    }
                    System.out.println("O maior nome é: " + maior);
                    break;

                case 8: // Substitui vogais por X em uma frase
                    System.out.println("Digite uma frase:");
                    String algo = scan.nextLine();
                    String substituida = algo.replaceAll("[aeiouAEIOU]", "X");
                    System.out.println("Frase modificada: " + substituida);
                    break;

                case 9: // Conta o número de vogais e consoantes
                    System.out.println("Digite uma frase:");
                    String texto = scan.nextLine();
                    int num_vogais = 0, num_consoantes = 0;
                    for (char c : texto.toCharArray()) {
                        if (Character.isLetter(c)) {
                            if ("aeiouAEIOU".indexOf(c) != -1) {
                                num_vogais++;
                            } else {
                                num_consoantes++;
                            }
                        }
                    }
                    System.out.println("Número de vogais: " + num_vogais);
                    System.out.println("Número de consoantes: " + num_consoantes);
                    break;

                case 10: // Verifica se uma palavra é palíndroma
                	System.out.println("Digite uma palavra:");
                    String palindroma = scan.nextLine();
                    boolean confirmacao = true; 
                    int tamanho = palindroma.length();
                    for (int i = 0; i < tamanho / 2; i++) { 
                        if (palindroma.charAt(i) != palindroma.charAt(tamanho - 1 - i)) { 
                            confirmacao = false; 
                            break;
                        }
                    }
                    if (confirmacao) {
                        System.out.println("A palavra é palíndroma!");
                    } else {
                        System.out.println("A palavra não é palíndroma.");
                    }
                    break;



                case 11: // Criptografa uma frase
                    System.out.println("Digite uma frase:");
                    String fraseParaCriptografar = scan.nextLine();
                    String criptografada = fraseParaCriptografar
                        .replace('A', 'X').replace('a', 'x')
                        .replace('E', 'Y').replace('e', 'y')
                        .replace('I', 'W').replace('i', 'w')
                        .replace('O', 'K').replace('o', 'k')
                        .replace('U', 'Z').replace('u', 'z');
                    System.out.println("Frase criptografada: " + criptografada);
                    break;

                case 12: // Sair do programa
                    System.out.println("Encerrando o programa...");
                    break;

                default:
                    System.out.println("Desculpa, essa opção não está no menu!");
                    break;
            }
        }

        scan.close();
    }
}
~~~


###Menu de Cadastro de Contato
~~~java
import java.util.ArrayList;
import java.util.Scanner;
public class exercicio102 {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        ArrayList<String> nomes = new ArrayList<>();
        ArrayList<String> telefone = new ArrayList<>();
        ArrayList<String> endereço = new ArrayList<>();
        ArrayList<String> aniversario = new ArrayList<>();
        ArrayList<String> email = new ArrayList<>();

        int indice = 0;

        while (true){
        //Aba do menu
        System.out.printf("Digite o número do menu:\n 0 Sair\n 1 Cadastrar um contato \n 2 Buscar um contato pelo nome \n 3 Mostrar aniversariantes do mês \n 4 Buscar contato pelo telefone \n 5 Mostrar total de cadastros \n 6 Atualizar dados de um cadastro \n");
        int opcao = scan.nextInt();

        if(opcao == 0){
            break;
        }
        else{
            switch (opcao) {
                case 1://cadastrar contato

                    System.out.print("Digite o nome do contato --> ");
                    String nome = scan.next();
                    nomes.add(nome);
                    System.out.print("Digite o telefone do contato --> ");
                    String tel = scan.next();
                    telefone.add(tel);
                    System.out.print("Digite o endereço do contato --> ");
                    String end = scan.next();
                    endereço.add(end);
                    System.out.print("Digite o aniversario do contato --> ");
                    String ani = scan.next();
                    aniversario.add(ani);
                    System.out.print("Digite o e-mail do contato --> ");
                    String mail = scan.next();
                    email.add(mail);
                    System.out.println("Contato cadastrado com sucesso");

                    for (int i = 0; i < nomes.size(); i++){
                        System.out.println(nomes.get(i));
                        System.out.println(telefone.get(i));
                        System.out.println(endereço.get(i));
                        System.out.println(aniversario.get(i));
                        System.out.println(email.get(i));
                    }
                        break;



                    case 2: // achar cadastro pelo nome
                    System.out.println("Entre com o nome que deseja procurar");
                    String procurado = scan.next();
                    for (String a : nomes){
                        if ( a.equals(procurado)){
                            indice = nomes.indexOf(a);
                            break;
                        }
                    }
                    System.out.printf("Informações do contato de nome %s\n telefone --> %s\n endereço --> %s\n aniversario --> %s\n email --> %s",procurado,telefone.get(indice),endereço.get(indice),aniversario.get(indice),email.get(indice));

                        break;
                      
                        

                    case 3:
                    System.out.println("Digite o mês (/mm/) em questão:");
                    String mes = scan.next();

                    for (String c : aniversario) {
                        // Comparando os caracteres referentes ao mês
                        if (mes.charAt(0) == c.charAt(3) && mes.charAt(1) == c.charAt(4)) {
                            System.out.printf("%s faz aniversário esse mês!%n", nomes.get(aniversario.indexOf(c)));
                        }
                    }
                        break; 


                    case 4: //achar cadastro pelo telefone
                    System.out.println("Entre com o telefone que deseja procurar");
                    String tel_procurado = scan.next();
                    for (String a : telefone){
                        if ( a.equals(tel_procurado)){
                            indice = telefone.indexOf(a);
                            break;
                        }
                    }
                    System.out.printf("Informações do contato de telefone %s\n nome --> %s\n endereço --> %s\n aniversario --> %s\n email --> %s",tel_procurado,nomes.get(indice),endereço.get(indice),aniversario.get(indice),email.get(indice));
                    
                        break;  
                    


                    case 5: // quantos contatos
                        int tamanho = nomes.size();
                        System.out.println("O total de cadastro é --> " + tamanho);
                        
                        break;  
                    

                        
                    case 6: //atualizar o cadastro
                        System.out.println("Entre com o nome atual do cadastro que deseja alterar:");
                        String alterar = scan.next();
                        for (String b : nomes){
                            if(b.equals(alterar)){
                                indice = nomes.indexOf(b);
                            }
                        }
                       
                        System.out.printf("Você deseja alterar nome?\n Digite true para sim\n Aperte false para não");
                        boolean escolha = scan.nextBoolean();
                        if(escolha == true){
                            System.out.println("Digite a alteração -->");
                            String novo = scan.next();
                            nomes.set(indice, novo);
                            System.out.println("Nome alterado");
                        }
                        
                        System.out.printf("Você deseja alterar telefone?\n Digite true para sim\n Aperte false para não");
                        escolha = scan.nextBoolean();
                        if(escolha == true){
                            System.out.println("Digite a alteração -->");
                            String novo = scan.next();
                            telefone.set(indice, novo);
                            System.out.println("Telefone alterado");
                        }
                    
                        System.out.printf("Você deseja alterar endereço?\n Digite true para sim\n Aperte false para não");
                        escolha = scan.nextBoolean();
                        if(escolha == true){
                            System.out.println("Digite a alteração -->");
                            String novo = scan.next();
                            endereço.set(indice, novo);
                            System.out.println("endereço alterado");
                        }

                        System.out.printf("Você deseja alterar aniversário?\n Digite true para sim\n Aperte false para não");
                        escolha = scan.nextBoolean();
                        if(escolha == true){
                            System.out.println("Digite a alteração -->");
                            String novo = scan.next();
                            aniversario.set(indice, novo);
                            System.out.println("aniversario alterado");
                        }
                        System.out.printf("Você deseja alterar e-mail?\n Digite true para sim\n Aperte false para não");
                        escolha = scan.nextBoolean();
                        if(escolha == true){
                            System.out.println("Digite a alteração -->");
                            String novo = scan.next();
                            email.set(indice, novo);
                            System.out.println("E-mail alterado");
                        }

                        break;

                    default:
                        System.out.println("Desculpa, essa  opção não está no menu");
        }}
    }
        

    }
    
}
~~~
