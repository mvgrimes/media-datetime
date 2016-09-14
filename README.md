# NAME

Media::DateTime - A simple module to extract the timestamp from media files in an flexible manner.

# VERSION

version 0.49

# SYNOPSIS

    use DateTime;
    use Media::DateTime;
    my $dt = Media::DateTime->datetime( $file );
    
    # or more cleanly OO
    my $dater = Media::DateTime->new;
    my $dt = $dater->datetime( $file );

# DESCRIPTION

Provides a very simple, but highly extensible method of extracting the
creation date and time from a media file (any file really). The base
module comes with support for JPEG files that store the creation date 
in the exif header. 

Plugins can be written to support any file format. See the 
`Media::DateTime::JPEG` module for an example.

If no plugin is found for a particular file (or the plugin returns 
a false vale) the file creation date as specified by the O/S is used.

Returns a `DateTime` object.

# METHODs

- new

    Constructor that returns a `Media::DateTime` object. Methods can be
    called on either the class or an instance.

            my $dt = Media::DateTime->new;

- datetime

    Takes a file as an arguement and returns a `DateTime` object representing
    its creation date. Falls back to the creation date specified by the 
    filesystem if no plugin is available.

            my $dt = Media::DateTime->datetime( $file );
            # or
            my $dt = $dater->datetime( $file );

# SEE ALSO

See the excellent `DateTime` module which simplifies the handling of dates.
See `Module::Pluggable` and `Module::Pluggable::Ordered` which are used
to implement the plugin system. `Image::Info` is used to extract data from
JPEG files for the `Media::DateTime::JPEG` plugin.

Make sure you have configured the local time zone on your machine. See
`DateTime::TimeZone::Local` for information on how the timezone is 
determined.

# AUTHOR

Mark Grimes, <mgrimes@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2016 by Mark Grimes, <mgrimes@cpan.org>.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
