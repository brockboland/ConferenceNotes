# [CocoaConf Chicago 2016](http://cocoaconf.com/chicago-2016/home)

## [Practical Continuous Integration with Xcode Server](http://cocoaconf.com/chicago-2016/sessions/Continuous-Integration-Hardy)
Brian Hardy
@lyricsboy

Xcode server


https://github.com/czechboy0/Buildasaur
https://github.com/czechboy0/xcskarel
xcscontrol

----
## [Collections in Swift](http://cocoaconf.com/chicago-2016/sessions/Collections-in-Swift)
Nate Cook
https://github.com/natecook1000/Collections-in-Swift

Protocol-oriented programming

### The problem
Thanks to type inference, things aren't always as they appear
Examples: prefix and reverse methods on arrays return some weird type
Reversing an Int array results in ReverseRandomAccessCollection<Array<Int>>

### How swift collections work
Collection system:
	Sequences > Collections > Range replaceable collections

Sequence: series of values we can access one at a time

SequenceType
	generate method -> Generator
GeneratorType
	next method -> Element?

Subsequences do not always make a copy
Sequences can be infinite

##### Collections
- Sets
- Ranges
- Dictionaries
- Strings (kind of) 

Have all the abilities that sequences do
Provide indexed subscript access to their elements
Always get the same elements in the same order when iterating
Collections:
	Array
	String views
	Sets
	Dictionaries

CollectionType
	startIndex
	endIndex [not a valid index for the collection]
	subscript(i: Index) -> Generator.Element
		Need to implement range check yourself
		
Index types
	Forward index types: move forward through the collection only
	Bidirectional index type: move forward or backward
	Random access index types

When moving from sequence to collection:
	Repeatable, indexed access to elements
	Index-based subsequence methods
	Ranged subscript
	indices: all indices that are valid on the collection

When checking if a collection is empty: use isEmpty, not count > 0, since that can be more expensive

##### Range-replaceable collections
- Arrays
- Strings (kind of) 

Support arbitrary subrange replacement
http://swiftdoc.org/v2.2/protocol/RangeReplaceableCollectionType/

Array types
	Array
		interoperable with ObjC as NSArray
	Contiguous array
		Contiguous block of memory
		Not interoperable with ObjC

### New approaches
You could create a new array
	Array(reversedElements)
…but this creates a copy of the reversedElements ReverseRandomAccessCollection instead of using the existing data in memory

----
## [Debugging and Testing](http://cocoaconf.com/chicago-2016/sessions/Tyree-Debugging-and-Testing)
Walter Tyree

### Chisel
https://github.com/facebook/chisel
- pvc: print recursive description of a view controller
- pdocspath: Print the path to the application's Document directory
- pdata: Print the contents of an NSData object as a string


### LLVM
- apropos works in LLVM (like in bash)
- Can also just type help


### Beagle
- ObjC debugging tool: https://github.com/heardrwt/RHObjectiveBeagle
- Loader to attach to simulator: https://github.com/heardrwt/RHObjectiveBeagleLoader
- Helps find objects in memory, via search


### Roll your own
- Script LLDB with Python scripting: http://lldb.llvm.org/scripting.html
- Good start: custom summary (shows in the left pane of the debugger for any instances of the class)
- ~/.lldbinit

----
## [MVC-N](http://cocoaconf.com/chicago-2016/sessions/exploring-mvc-n)
Marcus Zarra

MVC with Networking

### Network controller
An NSOperationQueue property
An NSManagedObjectContext property


Dynamic bandwidth handling
	Track the bandwidth (request time/data size) and adjust operation queue size as appropriate
	Keep items in the queue prioritized

Cancel GET requests when app goes to background
	But start a background task for any POST/PATCH/PUT request

Operations are better than blocks for network operation

----
## [Being A Subject Matter Expert](http://cocoaconf.com/chicago-2016/sessions/Being-A-Subject-Matter-Expert)
Marcus Zarra

Contracting

It's not what you wear, it's how you wear it
beingg comfortable and confident goes a long way

Don't argue with other contractors
No one wins

Their code sucks
They know this, that's why you're there

Types of FTEs
- Awed
- Challenger
- Eager
- Lifer

Usually two types of projects
- Design phase
- Silver bullet ("oh god please solve our problem")
	- Keep focused on the problem you're there to fix, because there will be many others
	- Start with small fixes: quick wins, establish trust and credentials

How do you start?
- Write a book: proof that you know what you're talking about
- Speak at conferences: name in the back of mind of people when they need help later
- Post on StackOverflow
- Networking

----
## [Speeding up your iOS Development with Fastlane](http://cocoaconf.com/chicago-2016/sessions/Fastlane-Van-Order)
Jacob Van Order

https://github.com/jacobvanorder/FastlaneCocoaConf2016

https://github.com/fastlane/fastlane/blob/master/fastlane/docs/Actions.md


Gotchas
- Directories
	- Fast lane and actions run in the SRCROOT/fastlane directory
	- Tools runs in the SRCROOT
- Ruby and simulator are slow
