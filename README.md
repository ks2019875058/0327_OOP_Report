# 0327_OOP_Report
namespace LinkedList
{

    class Node //노드 클래스 정의
    {
        public int data; // 리스트에 들어갈 데이터
        public Node next; // 다음 리스트를 가르킬 포인터
        public Node(int inputData) // 노드객체틀
        {
            data = inputData;
            next = null;
        }
    }
    class LinkedList //LL class 생성
    {
        private Node First;

        public void addFirst(int data) // 리스트 처음에 추가하기
        {
            Node newnode = new Node(data); // 새로 넣을 객체 생성
            newnode.next = First; // 그 객체의 next를 First로 한다 (처음보다 앞으로 넣는다)
            First = newnode; // First 를 새로운 노드로 바꾼다
        }

        public int getFirst() // 처음꺼 읽어오기
        {
            if (First == null) // First == null이다 => data 없음
                return -1; // 없으면 -1 리턴
            return First.data; // 아니면 First data 읽기
        }

        public void deleteFirst() //처음 지우기
        {
            First = First.next; // 처음이 가르키는 포인터를 next로 옮겨서 링크를 끊는다
        }

        public void addLast(int data) // 마지막에 추가하기
        {
            Node newnode = new Node(data); // 객체 생성
            if (First == null) //First == null이다 => 리스트 비어있다
            {
                First = newnode; // 그럼 새로운 노드가 처음
                return;
            }
            Node node; // 노드 객체 생성
            node = First; // 노드 객체를 First에 넣는다
            while (node.next != null) // 노드의 다음 포인터가 가르키는 곳이 null => 마지막 일 때 까지 반복
            {
                node = node.next; // 다음으로 옮긴다.
            }
            node.next = newnode; // 마지막에 추가
        }

        public int getLast() // 마지막 읽어오기
        {
            Node node;
            node = First;
            if (node.next == null) //노드의 다음 포인터가 가르키는 곳이 null => 마지막 일 때 까지 반복
            {
                node = node.next;
            }
            return node.data; // 마지막 노드의 데이터 값을 반환
        }

        public void deleteLast()
        {
            Node node, prevnode; //  노드 이전노드 만든다
            node = First;
            prevnode = node; // 이전노드를 노드에 덮어쓴다
            if (node.next == null) // 마지막까지
            {
                prevnode = node; // 이전노드를 노드에 덮어쓴다
                node = prevnode.next;
            }
            prevnode.next = null; // 이전노드의 마지막을  null 로 만들어서 링크를 끊는다
        }

        public void DeleteNode(int data) // 노드 지우기
        {
            Node changeNode = First;
            Node prevNode = null;
            if (changeNode == null && changeNode.data == data)
            {
                First = changeNode.next; // 읽어올 노드를 노드의 다음으로 바꿈
                return;
            }
            while (changeNode == null)
            {
                prevNode = changeNode;
                changeNode = changeNode.next; // 덮어쓰기
            }
            prevNode.next = changeNode.next;
        }

        public void listPrint()
        {
            for (Node node = First; node != null; node = node.next)
            // 노드의 데이터가 null 이 아닐 때 반복
            {
                Console.Write(node.data + " ");// 데이터 출력하고 한칸 띄움
            }
            Console.WriteLine(); // 줄바꿈
        }
    }

    class Stack
    {
        private LinkedList list = new LinkedList();

        public void push(int data)
        {
            list.addFirst(data); // Stack push == LinkedList addFirst 
        }

        public int pop()
        {
            int node = list.getFirst(); // 퍼스트 가져온다
            list.deleteFirst(); // 마지막을 지운다
            return node; // 새로고침
        }

        public void stackPrint()
        {
            list.listPrint();
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("----------------------------링크드 리스트----------------------------");

            LinkedList list = new LinkedList();

            Console.WriteLine("addFirst(1) 실행 후 리스트");
            list.addFirst(1);
            list.listPrint();

            Console.WriteLine("addLast(2) 실행 후 리스트");
            list.addLast(2);
            list.listPrint();

            Console.WriteLine("addFirst(3) 실행 후 리스트");
            list.addLast(3);
            list.listPrint();

            Console.WriteLine("addFirst(777) 실행 후 리스트");
            list.addFirst(777);
            list.listPrint();

            Console.WriteLine("----------------------------스택----------------------------");

            Stack stack = new Stack();

            Console.WriteLine("push(1) 실행");
            stack.push(1);

            Console.WriteLine("push(2) 실행");
            stack.push(2);

            Console.WriteLine("push(3) 실행");
            stack.push(3);

            Console.WriteLine("push(777) 실행");
            stack.push(777);

            Console.Write("\n");
            Console.WriteLine("현재 스택");
            stack.stackPrint();
            Console.Write("\n");


            Console.WriteLine("pop() 실행");
            Console.WriteLine(stack.pop());
            Console.WriteLine("현재 스택");
            stack.stackPrint();
            Console.Write("\n");

            Console.WriteLine("pop() 실행");
            Console.WriteLine(stack.pop());
            Console.WriteLine("현재 스택");
            stack.stackPrint();
            Console.Write("\n");

            Console.WriteLine("pop() 실행");
            Console.WriteLine(stack.pop());
            Console.WriteLine("현재 스택");
            stack.stackPrint();
            Console.Write("\n");

            Console.WriteLine("pop() 실행");
            Console.WriteLine(stack.pop());
            Console.WriteLine("현재 스택");
            stack.stackPrint();
            Console.Write("\n");
        }
    }
}
