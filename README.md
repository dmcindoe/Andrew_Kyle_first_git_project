# "My 4 Favorite Ruby methods"

### `Array`
An Array is an ordered, integer-indexed collection of objects, called elements. Any object may be an Array element.
```Ruby
Array.new(3)       #=> [nil, nil, nil]
```

### `Dir`
Objects of class Dir are directory streams representing directories in the underlying file system. They provide a variety of ways to list directories and their contents. See also File.
```Ruby
Dir.chdir("/var/spool/mail")
puts Dir.pwd
Dir.chdir("/tmp") do
  puts Dir.pwd
  Dir.chdir("/usr") do
    puts Dir.pwd
  end
  puts Dir.pwd
end
puts Dir.pwd
```

### `Warning`

The Warning module contains a single method named warn, and the module extends itself, making #warn available. #warn is called for all warnings issued by Ruby. By default, warnings are printed to $stderr.

Changing the behavior of #warn is useful to customize how warnings are handled by Ruby, for instance by filtering some warnings, and/or outputting warnings somewhere other than $stderr.
```Ruby
module MyWarningFilter
  def warn(message, category: nil, **kwargs)
    if /some warning I want to ignore/.matches?(message)
      # ignore
    else
      super
    end
  end
end
Warning.extend MyWarningFilter
```

### `Thread`
Threads are the Ruby implementation for a concurrent programming model.

Programs that require multiple threads of execution are a perfect candidate for Ruby's Thread class.
```Ruby
thr = Thread.new { puts "What's the big deal" }
```

