class Node(object):

    def __init__(self, item):
        self.item = item
        self.next = None

class SingleLinkList(Node):


#之前按照书上的代码，这个地方没有继承上面的类(Node),导致出现了AttributeError: 'NoneType' object has no attribute 'next'的错误，尝试了两
#种方法第一种是上面👆继承Node的方法，此时代码可以执行下去。第二种方法，我采用将while cur.next is not None:中的next改为_next，将其变成普通类
#成员的方法，代码也可以继续执行。

        def __init__(self,node = None):
        self.__head = node


    def is_empty(self):
        """链表是否为空
        :return 如果链表为空 返回真
        """
        return self.__head is None



    def length(self):
        """链表长度"""
        cur = self.__head
        count = 0
        while cur is not None:
            count += 1
            cur = cur.next
        return count

    def travel(self):
        """遍历整个链表"""
        cur = self.__head
        while cur is not None:
            print(cur.item, end=" ")
            cur = cur.next
        print("")

    def add(self, item):
        """链表头部添加元素
        :param item: 要保存的具体数据
        """
        node = Node(item)
        node.next = self.__head
        self.__head = node

    def append(self, item):
        """链表尾部添加元素"""
        node = Node(item)
        # 如果链表为空，需要特殊处理
        if self.is_empty():
            self.__head = node
        else:
            cur = self.__head
            while cur.next is not None:
                cur = cur.next
            # 退出循环的时候，cur指向的尾结点
            cur.next = node

    def insert(self, pos, item):
        """指定位置添加元素"""
        # 在头部添加元素
        if pos <= 0:
            self.add(item)
        # 在尾部添加元素
        elif pos >= self.length():
            self.append(item)
        else:
            cur = self.__head
            count = 0
            while count < (pos - 1):
                count += 1
                cur = cur.next
            # 退出循环的时候，cur指向pos的前一个位置
            node = Node(item)
            node.next = cur.next
            cur.next = node

    def remove(self, item):
        """删除节点"""
        cur = self.__head
        pre = None
        while cur is not None:
            # 找到了要删除的元素
            if cur.item == item:
                # 在头部找到了元素
                if cur == self.__head:
                    self.__head = cur.next
                else:
                    pre.next = cur.next
                return
            # 不是要找的元素，移动游标
            pre = cur
            cur = cur.next

    def search(self, item):
        """查找节点是否存在"""
        cur = self.__head
        while cur is not None:
            if cur.item == item:
                return True
            cur = cur.next
        return False

    def reveres(self):
        """反转元素节点"""
        if self.is_empty() or self.length() <= 1:
            return
        j = 0
        while j < self.length() - 1:
            cur = self.__head
            for i in range(self.length() - 1):
                cur = cur.next
                if cur.next is None:
                    x = cur.item
                    self.remove(cur.item)
                    self.insert(j, x)
            j += 1
            
            
if __ name __ == "__ main __":


    sll = SingleLinkList()
    # ll.SingleLinkList()
    print(sll.is_empty())
    print(sll.length())

    sll.add(8)
    sll.append(1)
    sll.append(2)
    sll.append(3)
    sll.append(4)
    sll.append(5)
    sll.append(6)
    print(sll.is_empty())
    print(sll.length())


    print(sll.Travel())
