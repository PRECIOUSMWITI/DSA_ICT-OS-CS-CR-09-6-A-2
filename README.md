// STRUCTURE DEFINITION
BEGIN CLASS Node
    SET data
    SET next = NULL
    
    CONSTRUCTOR(value)
        data = value
        next = NULL
    END CONSTRUCTOR
END CLASS

// MAIN LOGIC
BEGIN CLASS SinglyLinkedList
    SET head = NULL

    // Function to add a new node at the end
    BEGIN FUNCTION insert(value)
        CREATE newNode WITH value
        
        IF head IS NULL THEN
            SET head = newNode
        ELSE
            SET temp = head
            WHILE temp.next IS NOT NULL DO
                SET temp = temp.next
            END WHILE
            SET temp.next = newNode
        END IF
    END FUNCTION

    // Function to print the entire list
    BEGIN FUNCTION display()
        SET current = head
        WHILE current IS NOT NULL DO
            PRINT current.data + " -> "
            SET current = current.next
        END WHILE
        PRINT "null"
    END FUNCTION

    // Main entry point
    BEGIN MAIN
        INITIALIZE list = NEW SinglyLinkedList()
        
        CALL list.insert(10)
        CALL list.insert(20)
        CALL list.insert(30)
        
        PRINT "Linked List Contents:"
        CALL list.display()
    END MAIN
END CLASS
